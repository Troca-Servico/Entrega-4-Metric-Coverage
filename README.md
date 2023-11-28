# Teste METRICS E COVERAGE

Este teste avalia a porcentagem do código-fonte que é abrangida pelos testes, proporcionando uma medida crucial conhecida como cobertura de código. Essa métrica desempenha um papel fundamental ao identificar áreas não testadas, permitindo uma avaliação mais precisa da eficácia dos testes aplicados. No contexto específico deste teste, a meta de cobertura estabelecida é de 30% para as classes, o que significa que a cobertura deverá ser sobre as classes nas quais os testes devem ser exercidos.

 ![image](https://github.com/Troca-Servico/Entrega-4-Metric-Coverage/assets/111398446/0f2c92ed-0d29-4718-8bcf-5364c95e06e8)

## View
Os resultados dos testes são altamente positivos, demonstrando que as classes AppView, Perfil e Serviço estão operando de acordo com as expectativas. Os métodos demonstraram uma manipulação precisa das entradas simuladas, entregando saídas apropriadas. A execução bem-sucedida dos testes JUnit para essas classes valida de forma eficaz a funcionalidade geral da aplicação. Esses resultados reforçam a confiança na integridade e desempenho do sistema.

 ![image](https://github.com/Troca-Servico/Entrega-4-Metric-Coverage/assets/111398446/95590b9f-440b-4337-82e3-aff02d9cbe88)


## Teste de Conexão – dbConnection

Avaliação do Teste de Conexão – dbConnection
Inicialmente, o teste enfrentou um problema de configuração, uma vez que estava comparando `` Connection expResult = null; com Connection result = instance.getConnection(); usando assertEquals(expResult, result);``. Isso resultou em falhas, a menos que ``instance.getConnection() também retornasse null``. Para garantir o sucesso da conexão, foi necessário realizar a comparação utilizando assertNotEquals ou assertNotNull. Esta correção visa evitar falsos positivos e assegurar que a validação da conexão seja realizada de maneira adequada, contribuindo para a confiabilidade do teste e a precisão na detecção de falhas na conexão do banco de dados.

![image](https://github.com/Troca-Servico/Entrega-4-Metric-Coverage/assets/111398446/6b27a1c4-4c70-4bdc-8246-0726669a487d)


## Perfil – dbPerfil

O sistema oferece funcionalidades para cadastrar, visualizar, atualizar e excluir perfis, armazenando as informações de forma segura em um banco de dados MySQL. São implementados testes automatizados com o objetivo de assegurar o correto funcionamento das operações de salvar, buscar, atualizar e excluir perfis, contribuindo assim para a robustez e confiabilidade do sistema

## Servico – dbServico

Os testes realizados para a classe foram bem-sucedidos, apontando para uma implementação precisa da conexão com o banco de dados e das operações CRUD. Evidencia-se que a classe é capaz de interagir de maneira eficaz com o banco de dados, garantindo o salvamento e recuperação adequados das informações relacionadas aos serviços. 

![image](https://github.com/Troca-Servico/Entrega-4-Metric-Coverage/assets/111398446/5cdba81b-4f02-4b3a-bfe1-77bad0c413a0)

## Controller

Os testes realizados para as classes Controller, PerfilController e ServicoController foram concluídos com sucesso, evidenciando que as operações desses controladores estão alinhadas com as expectativas estabelecidas.

![image](https://github.com/Troca-Servico/Entrega-4-Metric-Coverage/assets/111398446/d6e97700-3ad3-4684-b3f5-b5f23d223c78)


## Model

Os testes foram concluídos com êxito, sinalizando que a implementação das classes Perfil e Serviço está correta, oferecendo os métodos de acesso esperados para seus atributos. A implementação demonstra robustez, proporcionando uma estrutura adequada para representar perfis no contexto do aplicativo de troca de serviços. É digno de nota que a cobertura alcançada foi de 59% e 100%, indicando uma abrangência significativa nos testes realizados, o que contribui para a confiança na funcionalidade e integridade das classes.

![image](https://github.com/Troca-Servico/Entrega-4-Metric-Coverage/assets/111398446/cc42daf6-5b48-4c55-b034-24d1fcf0aa94)

 
## Troca de Serviços
Estes testes foram bem- sucedidos, no qual o  Sistema de Troca de Serviços, realizado entre um usuário e outro chegando numa cobertura de 70% do código;

![image](https://github.com/Troca-Servico/Entrega-4-Metric-Coverage/assets/111398446/7a5b39fd-6ea0-483d-90bb-75e081409535)


# Teste METRICS

Teste de Metrics Concluído com Sucesso. O teste de Metrics foi executado com êxito no código do Sistema de Troca de Serviços, e nenhuma falha foi identificada durante a análise. Todos os aspectos avaliados apresentaram resultados conforme esperado, validando assim a integridade e a eficácia do sistema. Este resultado positivo reforça a confiança na qualidade e no desempenho do código do Sistema de Troca de Serviços.

![image](https://github.com/Troca-Servico/Entrega-4-Metric-Coverage/assets/111398446/e9e1dc14-5b8e-4df3-a601-15865a2d228c)
