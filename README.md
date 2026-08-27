# Atividade Prática: Pipeline CI/CD com Python e GitHub Actions

**Aluno:** Arthur Geraldo Santos Silva  
**R.A.:** 4251924719  
**Disciplina:** Garantia da Qualidade de Software  

---

## Descrição
Este repositório contém a atividade prática da disciplina de Garantia da Qualidade de Software. O objetivo principal é demonstrar a implementação de um pipeline automatizado que integra a execução de testes (Continuous Integration) e a geração de artefatos (Continuous Delivery), atuando como um Quality Gate.

## Respostas do Desafio

**1. O que representa a etapa de CI neste projeto?**
Representa o processo de integração e validação automatizada. A cada nova submissão de código ao repositório central, o GitHub Actions provisiona o ambiente e executa os testes de unidade. Este ciclo fornece um feedback imediato sobre a integridade da base de código, garantindo que novos incrementos não corrompam regras de negócio já estabelecidas.

**2. O que impede a execução do Continuous Delivery quando existe um defeito?**
O impedimento ocorre devido à diretiva `needs: ci` presente na estruturação do arquivo YAML. Tal diretriz formaliza uma dependência rigorosa: a etapa de Continuous Delivery só está autorizada a ser inicializada mediante a conclusão bem-sucedida da etapa de Continuous Integration.

**3. Qual seria a próxima etapa necessária para transformar este pipeline em Continuous Deployment?**
Para alcançar o nível de Continuous Deployment, faz-se necessária a implementação de uma etapa final (Deploy), encarregada de extrair o artefato validado pela fase de CD e publicá-lo automaticamente em ambiente de produção (seja um servidor cloud, serviço de hospedagem ou cluster de containers). A principal característica dessa evolução é a eliminação total de intervenções manuais no roteamento do código até o usuário final.

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
