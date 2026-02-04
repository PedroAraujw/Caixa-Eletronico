# Caixa Eletrônico (ATM)

Estudo de caso de **Engenharia de Software**, com foco em **Projeto Orientado a Objetos (OOD)**, utilizando a simulação de um caixa eletrônico como domínio do problema.

O projeto foi desenvolvido em **C++** e tem caráter **acadêmico**.

---

## Objetivo

Aplicar conceitos básicos de **orientação a objetos** e organização de software por meio da modelagem de um sistema bancário simples.

---

## Funcionalidades

- Consulta de saldo  
- Saque  
- Depósito  
- Interface via terminal

---

## Estrutura

    .
    ├── docs/        # Documentação e requisitos
    ├── include/     # Classes (.h)
    ├── src/         # Implementação (.cpp)
    ├── build/       # Arquivos gerados
    ├── README.md
    └── LICENSE #MIT

---

## Documentação UML

A modelagem do sistema foi realizada utilizando **PlantUML**, permitindo que os diagramas UML sejam descritos de forma textual e versionados junto ao código-fonte.

Os diagramas fazem parte do estudo de caso e encontram-se no diretório `docs/uml/`.

---

## Nota

O projeto deve ser analisado sob a perspectiva de **engenharia de software e OOD**,
e não como um sistema bancário real.

---

## Compilação

    g++ -Iinclude src/*.cpp -o caixa_eletronico

## Execução

    ./caixa_eletronico

---

## Licença

MIT

