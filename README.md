# ScreenMatch

![Java](https://img.shields.io/badge/Java-25-orange?logo=openjdk&logoColor=white)
![Licença](https://img.shields.io/badge/licença-MIT-blue)
![Status](https://img.shields.io/badge/status-em%20desenvolvimento-yellow)

Projeto de estudos desenvolvido durante os cursos de **Java** da [Alura](https://www.alura.com.br/), na formação de Orientação a Objetos.

O ScreenMatch é um catálogo simples de filmes e séries que serve de laboratório para praticar os pilares da OO: classes, encapsulamento, herança, polimorfismo e interfaces.

## Sobre o projeto

A aplicação é um programa de console que:

- cadastra **filmes** e **séries** com nome, ano de lançamento e duração;
- registra **avaliações** e calcula a média de notas de um título;
- calcula a **duração total de maratona** de uma série (temporadas × episódios × minutos);
- soma o **tempo total** de uma lista de títulos de tipos diferentes com uma única calculadora;
- **recomenda** títulos e episódios a partir de uma classificação, usando uma interface comum.

## Conceitos de OO aplicados

| Conceito | Onde aparece |
|---|---|
| **Classes e encapsulamento** | `Titulo` guarda os atributos como `private` e expõe getters/setters |
| **Herança** | `Filme` e `Serie` estendem `Titulo` e reaproveitam o comportamento comum |
| **Polimorfismo (sobrescrita)** | `Serie.getDuracaoEmMinutos()` sobrescreve o cálculo herdado de `Titulo` |
| **Polimorfismo (parâmetros)** | `CalculadoraDeTempo.inclui(Titulo)` aceita qualquer subtipo de `Titulo` |
| **Interfaces** | `Classificavel` é implementada por `Filme` e `Episodio`, permitindo que `FiltroRecomendacao` trabalhe com tipos sem relação de herança entre si |

## Estrutura do projeto

```
src/
└── br/com/alura/screenmatch/
    ├── Principal.java              # classe com o método main
    ├── calculos/
    │   ├── CalculadoraDeTempo.java # soma a duração de vários títulos
    │   ├── Classificavel.java      # interface de classificação
    │   └── FiltroRecomendacao.java # recomenda a partir da classificação
    └── modelos/
        ├── Titulo.java             # classe base (nome, ano, avaliações)
        ├── Filme.java              # título com diretor
        ├── Serie.java              # título com temporadas e episódios
        └── Episodio.java           # episódio de uma série
```

## Como executar

**Pré-requisito:** JDK 17 ou superior ([Java 25](https://adoptium.net/) foi usado no desenvolvimento).

### Pelo terminal

```bash
git clone https://github.com/eduardogazolla/ScreenMatch.git
cd ScreenMatch

# compila para a pasta out/
javac -encoding UTF-8 -d out $(find src -name "*.java")

# executa
java -cp out br.com.alura.screenmatch.Principal
```

No Windows (PowerShell), troque a linha de compilação por:

```powershell
javac -encoding UTF-8 -d out (Get-ChildItem -Recurse src -Filter *.java).FullName
```

### Pela IDE

Abra a pasta do projeto no IntelliJ IDEA (ou Eclipse/VS Code), marque `src` como *source root* e rode a classe `Principal`.

## Saída esperada

```
Duração do filme: 180
Nome do filme: O poderoso chefão
Ano de lançamento: 1970
Total de avaliações: 3
7.666666666666667
Nome do filme: Lost
Ano de lançamento: 2000
Duração para maratonar Lost: 5000
...
5380
Muito bem avaliado no momento!
Está entre os preferidos do momento
```

## Próximos passos

- [ ] Listar e ordenar títulos com `ArrayList` e `Comparable`
- [ ] Tratar entradas inválidas com exceções
- [ ] Ler dados de uma API externa (OMDb) e desserializar JSON
- [ ] Persistir os títulos em banco de dados com Spring Data JPA

## Licença

Distribuído sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

Feito por [Eduardo Gazolla](https://github.com/eduardogazolla) enquanto estudava Java na Alura.
