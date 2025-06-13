# sclgenerator

const N = parseInt(process.argv[2], 10);
if (!Number.isInteger(N) || N <= 0) {
  console.error('Error: N must be a positive integer'); //this is english wow thank u goggle tansulater
  process.exit(1);
}

const fileName = `${N}-EDO.scl`;
const headerLines = [
  `${N}`,
  '!',
];

const step = 1200 / N;
const intervalLines = [];
for (let i = 1; i <= N; i++) {
  const cents = parseFloat((step * i).toFixed(5)).toString(); //精度低い
  intervalLines.push(cents);
}

const content = headerLines.concat(intervalLines).join('\n');
fs.writeFileSync(fileName, content, 'utf8');
console.log(`Generated ${fileName}`);
