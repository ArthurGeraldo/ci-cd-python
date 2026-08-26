# Atividade Prática: Pipeline CI/CD com Python e GitHub Actions

**Aluno:** Arthur Geraldo Santos Silva
**R.A.:** 4251924719
**Disciplina:** Garantia da Qualidade de Software

---

## Descrição
Este repositório contém a atividade prática de laboratório da disciplina de Garantia da Qualidade de Software. O objetivo principal é demonstrar a implementação de um pipeline automatizado que integra a execução de testes (Continuous Integration) e a geração de artefatos (Continuous Delivery), atuando como um Quality Gate.

## Estrutura do Projeto

```
ci-cd-python/
│
├── calculadora.py            # Código-fonte da aplicação
├── test_calculadora.py       # Suíte de testes automatizados (pytest)
├── requirements.txt          # Dependências do projeto
└── .github/
    └── workflows/
        └── pipeline.yml      # Configuração do GitHub Actions
