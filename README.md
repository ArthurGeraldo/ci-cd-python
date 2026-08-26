Pipeline CI/CD com Python e GitHub Actions
Descrição

Este projeto foi desenvolvido como atividade prática da disciplina de Garantia de Software, com o objetivo de implementar um pipeline de Continuous Integration (CI) e Continuous Delivery (CD) utilizando Python e GitHub Actions.

A aplicação consiste em uma calculadora simples com operações de soma, subtração, multiplicação e divisão. Os testes automatizados são executados pelo pytest.

Estrutura do projeto
ci-cd-python/
├── calculadora.py
├── test_calculadora.py
├── requirements.txt
├── README.md
└── .github/
    └── workflows/
        └── pipeline.yml

Pipeline

O pipeline é executado automaticamente quando ocorre:

um push na branch main;
um pull request direcionado para a branch main.

O processo possui duas etapas principais:

Continuous Integration (CI)

A etapa de CI realiza:

Download do código do repositório;
Configuração do ambiente Python;
Atualização do pip;
Instalação das dependências;
Execução dos testes automatizados com pytest.

Se algum teste falhar, o job de CI será considerado como falho.

Continuous Delivery (CD)

A etapa de CD depende do sucesso da etapa de CI.

Quando o código da branch main é aprovado nos testes, o pipeline:

Baixa o código;
Cria uma pasta dist;
Copia o arquivo calculadora.py;
Cria um arquivo build-info.txt contendo o commit utilizado;
Publica esses arquivos como um artefato chamado calculadora-python.
Quality Gate

O teste automatizado funciona como um quality gate, ou seja, uma barreira de qualidade.

O job de Continuous Delivery possui a seguinte dependência:

needs: ci


Isso significa que o Delivery somente poderá ser executado se o job de CI for concluído com sucesso.

Durante a atividade, foi realizada uma alteração proposital no código para provocar uma falha em um teste. Com isso, foi possível observar que o CI ficou vermelho e o Continuous Delivery não foi executado.

Após corrigir o código, os testes foram executados novamente e o pipeline voltou a funcionar normalmente.

Perguntas da atividade
1. O que representa a etapa de CI neste projeto?

A etapa de CI representa a integração e validação automática do código. Sempre que ocorre um push ou pull request para a branch main, o GitHub Actions configura o ambiente Python, instala as dependências e executa os testes automatizados.

Dessa forma, possíveis erros no código podem ser identificados rapidamente antes que uma versão seja disponibilizada para entrega.

2. O que impede a execução do Continuous Delivery quando existe um defeito?

O que impede a execução do Continuous Delivery é a dependência definida por:

needs: ci


O job de Delivery depende do sucesso do job de CI. Portanto, quando um teste falha, o CI fica com status de falha e o Delivery não é executado.

Isso funciona como um quality gate, impedindo que um código que não passou pelos testes gere uma versão para entrega.

3. Qual seria a próxima etapa necessária para transformar este pipeline em Continuous Deployment?

Para transformar o pipeline em Continuous Deployment, seria necessário adicionar uma etapa de implantação automática após a aprovação dos testes e a geração do artefato.

Essa etapa poderia realizar o deploy da aplicação automaticamente em um servidor, serviço de nuvem ou outra plataforma de hospedagem.

A diferença é que, no Continuous Delivery, o software aprovado fica preparado para ser entregue, enquanto no Continuous Deployment a implantação também ocorre automaticamente.

Tecnologias utilizadas
Python
pytest
GitHub
GitHub Actions
Resultado esperado

Ao final da execução correta do pipeline:

Continuous Integration    ✅
Continuous Delivery       ✅
Artefato                  📦 calculadora-python


O artefato gerado contém a aplicação e as informações da versão utilizada no processo de entrega.
