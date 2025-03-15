# Instruções
- Faça uma cópia deste arquivo .md para um repositório próprio
- Resolva as 8 questões objetivas assinalando a alternativa correta e **justificando sua resposta.**
- Resolva as 2 questões dissertativas escrevendo no próprio arquivo .md
- Lembre-se de utilizar as estruturas de código como ``esta aqui com ` `` ou
```javascript
//esta aqui com ```
let a = "olá"
let b = 10
print(a)
```
- Resolva as questões com uso do Visual Studio Code ou ambiente similar.
- Teste seus códigos antes de trazer a resposta para cá.
- Cuidado com o uso de ChatGPT (e similares), pois entregar algo só para ganhar nota não fará você aprender. Não seja dependente da máquina!
- Ao final, publique seu arquivo lista_01.md com as respostas em seu repositório, e envie o link pela Adalove. 

# Questões objetivas
**1) Considerando a execução do código abaixo, indique a alternativa correta e justifique sua resposta.**
```javascript
console.log(x);
var x = 5;
console.log(y);
let y = 10;
```
a) A saída será undefined seguido de erro:

b) A saída será 5 seguido de 10

c) A saída será undefined seguido de undefined

d) A saída será erro em ambas as linhas que utilizam console.log

Resposta:
A alternativa correta é a A. Quando tentamos acessar a variável `x` antes da declaração, a saída será `undefined` devido ao conceito de hoisting no JavaScript, onde variáveis declaradas com `var` são movidas para o topo do escopo, mas sem atribuição de valor. Já para a variável `y`, declarada com `let`, ocorre um erro, pois `let` e `const não permitem acesso antes da inicialização.

**2) O seguinte código JavaScript tem um erro que impede sua execução correta. Analise e indique a opção que melhor corrige o problema. Justifique sua resposta.**
```javascript
function soma(a, b) {
    if (a || b === 0) {
        return "Erro: número inválido";
    }
    return a + b;
}
console.log(soma(2, 0));
```
a) Substituir if (a || b === 0) por if (a === 0 || b === 0)

b) Substituir if (a || b === 0) por if (a === 0 && b === 0)

c) Substituir if (a || b === 0) por if (a && b === 0)

d) Remover completamente a verificação if (a || b === 0)

Resposta:
A resposta correta é a alternativa B. O código pretende verificar se os dois valores passados para a função são `0`, e nesse caso, retornar um erro. No código original, a verificação `a || b === 0` não está correta, pois `b === 0` será avaliado primeiro, mas `a` sempre será tratado como um valor booleano. A correção necessária é usar `a === 0 && b === 0`, garantindo que apenas quando ambos forem zero o erro seja retornado.

_____
**3) Ao executar esse código, qual será a saída no console? Indique a alternativa correta e justifique sua resposta.**
```javascript
function calcularPreco(tipo) {
    let preco;

    switch(tipo) {
        case "eletrônico":
            preco = 1000;
        case "vestuário":
            preco = 200;
            break;
        case "alimento":
            preco = 50;
            break;
        default:
            preco = 0;
    }

    return preco;
}

console.log(calcularPreco("eletrônico"));
```
a) O código imprime 1000.

b) O código imprime 200.

c) O código imprime 50.

d) O código gera um erro.

Resposta:
A resposta correta é a alternativa B. Apesar de o case `"eletrônico"` definir `preco = 1000`, a falta do `break` faz com que a execução continue para o próximo `case`, sobrescrevendo `preco` com `200` antes de sair do `switch`. Isso causa um comportamento inesperado e retorna `200` como resultado final.

_____
# Questões dissertativas
**9) O seguinte código deve retornar a soma do dobro dos números de um array, mas contém erros. Identifique os problemas e corrija o código para que funcione corretamente. Adicione comentários ao código explicando sua solução para cada problema.**
```javascript
function somaArray(numeros) {
    const tamanho = numeros.length; // Defini uma variável para armazenar o tamanho do array
    let soma = 0; // Inicializei a variável soma para evitar referência a um valor indefinido
    for (let i = 0; i < tamanho; i++) { // Corrigi a declaração da variável i, que estava sem let
        soma += numeros[i]; // Somo os valores corretamente
    }
    return soma * 2; // Multiplico o resultado final por 2
}
console.log(somaArray([1, 2, 3, 4])); // Imprime o resultado no console
```
_____
**10) Crie um exemplo prático no qual você tenha duas classes:**

- Uma classe `Produto` com atributos `nome` e `preco`, e um método `calcularDesconto()` que aplica um desconto fixo de 10% no preço do produto.
- Uma classe `Livro` que herda de `Produto` e modifica o método `calcularDesconto()`, aplicando um desconto de 20% no preço dos livros.

Explique como funciona a herança nesse contexto e como você implementaria a modificação do método na classe `Livro`.
```javascript
class Produto {
    constructor(nome, preco) {
        this.nome = nome;
        this.preco = preco;
    }
    calcularDesconto() {
        return this.preco * 0.9;
    }
}

class Livro extends Produto {
    calcularDesconto() {
        return this.preco * 0.8;
    }
}

const produto = new Produto("Celular", 1000);
console.log(produto.calcularDesconto()); // Saída: 900

const livro = new Livro("Harry Potter", 50);
console.log(livro.calcularDesconto()); // Saída: 40
```
A herança permite que a classe `Livro` reutilize os atributos da classe `Produto`, sem precisar redefinir `nome` e `preco`. No entanto, o método `calcularDesconto()` é sobrescrito na classe `Livro`, aplicando um desconto diferente, demonstrando um caso de polimorfismo.
