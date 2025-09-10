<template>
    <h1>{{ the.title }}</h1>
    <p>{{ the.description }}</p>
    <el-divider></el-divider>
    <dl class="grid grid-cols-2 gap-x-4 w-fit not-prose">
        <dt class="font-bold text-right">Адрес репозитория:</dt>
        <dd><a href="https://github.com/vuebro/flat-json-tree" target="_blank" class="underline">https://github.com/vuebro/flat-json-tree</a></dd>
        <dt class="font-bold text-right">Стек технологий:</dt>
        <dd>Vue</dd>
        <dt class="font-bold text-right">Решаемая задача:</dt>
        <dd>Удобный и быстрый поиск а также манипуляции с элементами JSON дерева</dd>
    </dl>
    <p>JSON дерево представляет из себя массив объектов следующего вида (пример совершенно абстрактный):</p>
    <highlightjs language="json" :code="code1" class="pa-0 -mx-4"></highlightjs>
    <p>В нём, как в матрешке сложены объекты с произвольным набором аттрибутов. Для нашего примера, условимся лишь, что
        у каждого элемента есть уникальный id и дочерние элементы записываюся в массив children.</p>
    <p>Как правило, для поиска по таким деревьям используется JSON tree traversal (обход JSON-дерева) — это процесс
        последовательного посещения или обработки каждого узла JSON-структуры (которая является деревом) ровно один раз.
        По сути, это алгоритм, который позволяет пройти по всем элементам данных в JSON-объекте или массиве, чтобы
        выполнить определенные действия, например, найти, извлечь или обновить значения.
    </p>
    <p>При этом в javascript нет встроенного инструментария для работы с JSON деревьями. А ведь правда было бы зорово,
        чтобы с ними можно было работать как с обычными <a
            href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array"
            target="_blank">массивами</a>, используя стандартные методы для фильтрации, поиска, сортировки и т.д.</p>
    <p>@vuebro/flat-json-tree как раз реализует идею "сплющивания" - "JSON tree flatt" (flatten). Как результат, все
        элементы дерева выстраиваются в обычный массив. Для примера, дерево приведенное выше, будет выглядеть так:</p>
    <highlightjs language="json" :code="code2" class="pa-0 -mx-4"></highlightjs>
    <p>В нем все 9 элементов выстраиваются в плоский массив, не теряя при этом своих дочерних элементов. Это позволяет
        провести быстрый поиск по массиву обычными средствами. К примеру, найдем объект с name = "1.2.6":</p>
    <highlightjs language="javascript" :code="code3" class="pa-0 -mx-4"></highlightjs>
    <p>Но грош цена такому поиску, если невозможно определить положение найденного элемента в дереве. Поэтому,
        @vuebro/flat-json-tree для каждого элемента добавляет вычисляемые параметры, однозначно определяющие его позицию
        в JSON дереве:</p>
    <highlightjs language="javascript" :code="code4" class="pa-0 -mx-4"></highlightjs>
    <p>Возвращаясь к нашему примеру, необходимо просто считать нужный параметр у найденного объекта. К примеру - obj.parent вычислит его родительский элемент.</p>
    <p>Результируя, приведу пример использования @vuebro/flat-json-tree:</p>
    <highlightjs language="javascript" :code="code5" class="pa-0 -mx-4"></highlightjs>
    <p>Где композабл useFlatJsonTree возвращает:</p>
    <highlightjs language="javascript" :code="code6" class="pa-0 -mx-4"></highlightjs>
</template>

<script setup lang="js">
import { inject } from 'vue';

const { pid } = defineProps(["pid"]),
    the = inject("pages")[pid],
    code1 = `[
  {
    "id": 1,
    "name": "root",
    "children": [
      {
        "id": 2,
        "name": "1.2",
        "children": [
          { "id": 5, "name": "1.2.5" },
          { "id": 6, "name": "1.2.6" },
        ],
      },
      { "id": 3, name: "1.3" },
      {
        "id": 4,
        "name": "1.4",
        "children": [
          { "id": 7, "name": "1.4.7" },
          { "id": 8, "name": "1.4.8" },
          { "id": 9, "name": "1.4.9" },
        ],
      },
    ],
  },
];`,
    code2 = `[
  {
    "id": 1,
    "name": "root",
    "children": [ ... ]
  },
  {
    "id": 2,
    "name": "1.2",
    "children": [ ... ]
  },
  { "id": 5, "name": "1.2.5" },
  { "id": 6, "name": "1.2.6" },
  { "id": 3, "name": "1.3" },
  {
    "id": 4,
    "name": "1.4",
    "children": [ ... ]
  },
  { "id": 7, "name": "1.4.7" },
  { "id": 8, "name": "1.4.8" },
  { "id": 9, "name": "1.4.9" }
]`,
    code3 = 'const obj = arrLeaves.find(({ name }) => name === "1.2.6")',
    code4 = `{
  // Массив объектов, представляющий из себя путь от корня до текущего элемента
  branch: Record < string, unknown > [];
  // Порядок объекта в массиве объектов на текущем уровне дерева
  index: number;
  // Следующий объект массиве объектов на текущем уровне дерева
  next: Record<string, unknown> | undefined;
  // Родительский объект
  parent: Record<string, unknown> | undefined;
  // Предыдущий объект массиве объектов на текущем уровне дерева
  prev: Record<string, unknown> | undefined;
  // Массив объектов на текущем уровне дерева
  siblings: Record < string, unknown > [];
}`,
code5 = `import useFlatJsonTree from "@vuebro/flat-json-tree";

const tree = [
  {
    id: 1,
    name: "root",
    children: [
      {
        id: 2,
        name: "1.2",
        children: [
          { id: 5, name: "1.2.5" },
          { id: 6, name: "1.2.6" },
        ],
      },
      { id: 3, name: "1.3" },
      {
        id: 4,
        name: "1.4",
        children: [
          { id: 7, name: "1.4.7" },
          { id: 8, name: "1.4.8" },
          { id: 9, name: "1.4.9" },
        ],
      },
    ],
  },
];

const { leaves, arrLeaves, objLeaves, add, down, left, remove, right, up } =
  useFlatJsonTree(tree);`,
  code6 = `{
  // Вычисленный плоский массив объектов (доступ через .value)
  leaves: ComputedRef<Record<string, unknown>[]>;
  // Реактивный вариант этого же массива
  arrLeaves: Record<string, unknown>[];
  // Реактивный объект всех элементов плоского массива с их ID в качестве ключей
  objLeaves: {[id: string]: Record<string, unknown>;};
  // Сервисная ф-ция добавления пустого объекта в дерево
  add: (pId: string) => string | undefined;
  // Сервисная ф-ция удаления объекта из дерева
  remove: (pId: string) => string | undefined;
  // Сервисная ф-ция для сдвига объекта вниз в дереве на одну позицию
  down: (pId: string) => void;
  // Сервисная ф-ция для сдвига объекта влево в дереве на одну позицию
  left: (pId: string) => string | undefined;
  // Сервисная ф-ция для сдвига объекта вправо в дереве на одну позицию
  right: (pId: string) => string | undefined;
  // Сервисная ф-ция для сдвига объекта вверх в дереве на одну позицию
  up: (pId: string) => void;
}`;

</script>
