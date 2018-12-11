---
title: Arquitetura sem servidor - aplicativos sem servidor
description: Exploração de várias arquiteturas e aplicativos que são compatíveis com arquiteturas sem servidor, incluindo aplicativos web, móveis e IoT.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 5f22f8b9894a23e5920adb2af3fdf02bce2877d7
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150297"
---
# <a name="serverless-architecture"></a>Arquitetura sem servidor

Há muitas abordagens para usando arquiteturas sem servidor. Este capítulo explora os exemplos de arquiteturas comuns que se integram sem servidor. Ele também aborda questões que podem apresentar desafios adicionais ou exigir maior consideração ao implementar sem servidor. Por fim, vários exemplos de design são fornecidas que ilustram vários casos de uso sem servidor.

Hosts sem servidor geralmente usam um existentes baseados em contêiner ou a camada do PaaS para gerenciar as instâncias sem servidor. Por exemplo, o Azure Functions se baseia [serviço de aplicativo do Azure](https://docs.microsoft.com/azure/app-service/). O serviço de aplicativo é usado para expandir as instâncias e gerenciar o tempo de execução que executa o código do Azure Functions. Para funções com base em Windows, as execuções de host como PaaS e escalas de reduzir o tempo de execução do .NET. Para funções com base em Linux, o host utiliza contêineres.

![Arquitetura de funções do Azure](./media/azure-functions-architecture.png)

O núcleo de trabalhos Web fornece um contexto de execução para a função. O tempo de execução de linguagem executa scripts, executa a bibliotecas e hospeda a estrutura para o idioma de destino. Por exemplo, Node. js é usado para executar funções do JavaScript e o .NET Framework é usado para executar funções do c#. Você aprenderá mais sobre as opções de idioma e plataforma neste capítulo.

Alguns projetos podem se beneficiar de adotar uma abordagem "totalmente em" para o sem servidor. Aplicativos que dependem muito de microsserviços podem implementar todos os microsserviços usando a tecnologia sem servidor. A maioria dos aplicativos são híbridas, seguindo um design de N camadas e usando sem servidor para os componentes que fazem sentido porque os componentes são modular e escalonável de maneira independente. Para ajudar a dar sentido a esses cenários, esta seção orienta por meio de alguns exemplos comuns de arquitetura que usar sem servidor.

## <a name="full-serverless-back-end"></a>Back-end completa sem servidor

O back-end completa sem servidor é ideal para vários tipos de cenários, especialmente ao criar novos ou aplicativos de "campo verde". Um aplicativo com uma grande área de superfície das APIs pode se beneficiar com a implementação de cada API como uma função sem servidor. Os aplicativos baseados em arquitetura de microsserviços são outro exemplo que pode ser implementado como um back-end sem servidor completo. Os microsserviços se comunicam por meio de vários protocolos entre si. Cenários específicos incluem:

* Produtos de SaaS baseado em API (exemplo: processador de pagamentos financeiro).
* Aplicativos orientados a mensagens (exemplo: solução de monitoramento de dispositivo).
* Aplicativos voltados para a integração entre serviços (exemplo: aplicativo de reservas de companhia aérea).
* Processos executados periodicamente (exemplo: banco de dados baseado em temporizador limpeza).
* Aplicativos voltados para transformação de dados (exemplo: importação disparada pelo upload de arquivo).
* Extraia os processos de transformação e carregamento (ETL).

Há casos de uso de outros, mais específicos são abordados neste documento.

## <a name="monoliths-and-starving-the-beast"></a>Monolitos e "privando a fera"

Um desafio comum está migrando um aplicativo monolítico existente para a nuvem. A abordagem menos arriscada é "lift and shift" inteiramente em máquinas virtuais. Vários departamentos de preferem usar a migração como uma oportunidade para modernizar sua base de código. Uma abordagem prática para a migração é chamada de "privando a fera". Nesse cenário, o monolito é migrado "como está" para começar. Em seguida, os serviços selecionados serão modernizados. Em alguns casos, a assinatura do serviço é idêntica ao original: ele simplesmente está hospedado como uma função. Os clientes são atualizados para usar o novo serviço em vez do ponto de extremidade monólito. Enquanto isso, etapas, como replicação de banco de dados permitem microsserviços hospedar seu próprio armazenamento, mesmo quando as transações ainda são manipuladas pelo monólito. Eventualmente, todos os clientes são migrados para os novos serviços. O monolito está "sem" (seus serviços não é mais chamados) até que toda a funcionalidade foi substituída. A combinação de sem servidor e proxies podem facilitar grande parte da migração.

![Migração de monólito sem servidor](./media/serverless-monolith-migration.png)

Para saber mais sobre essa abordagem, assista ao vídeo: [Traga o seu aplicativo para a nuvem com o Azure Functions sem servidor](https://channel9.msdn.com/Events/Connect/2017/E102).

## <a name="web-apps"></a>Aplicativos Web

Aplicativos Web são bons candidatos para aplicativos sem servidor. Há duas abordagens comuns para aplicativos web hoje: orientado para servidor e controlado por cliente (como aplicativo de página única ou SPA). Aplicativos web orientado para servidor normalmente usam uma camada de middleware emitir chamadas de API para renderizar a interface da web. Aplicativos SPA fazem chamadas à API REST diretamente do navegador. Em ambos os cenários sem servidor pode acomodar a solicitação da API REST ou middleware, fornecendo a lógica comercial necessária. É uma arquitetura comum criar um servidor web estático leve. O aplicativo de página única (SPA) serve HTML, CSS, JavaScript e outros ativos do navegador. O aplicativo web, em seguida, se conecta a um back-end de microsserviços.

## <a name="mobile-back-ends"></a>Back-ends móveis

O paradigma de aplicativos sem servidor orientada a eventos torna ideal como o back-ends móveis. O dispositivo móvel dispara os eventos e o código sem servidor é executado para atender às solicitações. Tirando proveito de um modelo sem servidor permite que os desenvolvedores aperfeiçoar a lógica de negócios sem a necessidade de implantar uma atualização de aplicativo completo. A abordagem sem servidor também permite que equipes compartilhar pontos de extremidade e trabalhem em paralelo.

Desenvolvedores de aplicativos móveis podem criar lógica de negócios sem se tornar especialistas no lado do servidor. Tradicionalmente, os aplicativos móveis conectados aos serviços de local. Criando a camada de serviço necessária Noções básicas sobre a plataforma de servidor e o paradigma de programação. Os desenvolvedores trabalharam com operações para provisionar servidores e configurá-los adequadamente. Às vezes, dias ou até mesmo semanas foram gastos na criação de um pipeline de implantação. Todos esses desafios são resolvidos por sem servidor.

Serverless abstrai as dependências do lado do servidor e permite que o desenvolvedor se concentre na lógica de negócios. Por exemplo, um desenvolvedor móvel que compila aplicativos usando uma estrutura JavaScript pode criar funções sem servidor com o JavaScript também. O host sem servidor gerencia o sistema operacional, uma instância de Node. js para hospedar o código, as dependências do pacote e muito mais. O desenvolvedor é fornecido um conjunto simples de entradas e um modelo padrão para saídas. Eles, em seguida, podem se concentrar em criar e testar a lógica de negócios. Eles são, portanto, podem usar habilidades existentes para criar a lógica de back-end para o aplicativo móvel sem precisar aprender novas plataformas ou se tornar um "desenvolvedor do lado do servidor".

![Término de volta móveis sem servidor](./media/serverless-mobile-backend.png)

A maioria dos provedores de nuvem oferecem produtos sem servidor com base em mobile que simplificam o ciclo de vida inteiro de desenvolvimento móvel. Os produtos podem automatizar o provisionamento de bancos de dados para manter os dados, lidar com preocupações de DevOps, fornecer baseado em nuvem compilações e testes de estruturas e a capacidade de processos de negócios de script usando o desenvolvedor o idioma preferencial. Seguir uma abordagem centrada em mobile de sem servidor pode simplificar o processo. Sem servidor remove a enorme sobrecarga de provisionamento, configuração e manutenção de servidores para o back-end móvel.

## <a name="internet-of-things-iot"></a>IoT (Internet das Coisas)

IoT refere-se aos objetos físicos que são conectados em rede. Eles são chamados de "dispositivos conectados" ou "dispositivos inteligentes". Tudo, de carros e máquinas de venda automáticas podem ser conectados e enviar informações variando de inventário para dados de sensor, como temperatura e umidade. Na empresa, IoT fornece melhorias no processo de negócios por meio de monitoramento e automação. Dados de IoT podem ser usados para regular a clima em um depósito grande ou acompanhar o inventário por meio da cadeia de fornecimento. IoT pode detectar vazamentos químicos e chamar o departamento de incêndio quando fumaça é detectada.

O volume total de dispositivos e informações geralmente determina uma arquitetura orientada a eventos para mensagens de rota e de processo. Sem servidor é uma solução ideal por vários motivos:

* Escala permite que o volume de dados e dispositivos aumenta.
* Acomoda a adição de novos pontos de extremidade para dar suporte a novos dispositivos e sensores.
* Facilita o controle de versão independente para que os desenvolvedores podem atualizar a lógica de negócios para um dispositivo específico sem precisar implantar o sistema inteiro.
* Resiliência e menor tempo de inatividade.

A abrangência do IoT resultou em vários produtos sem servidor que se concentram especificamente em questões de IoT, tais como [IoT Hub do Azure](https://docs.microsoft.com/azure/iot-hub). Serverless automatiza tarefas, como o registro de dispositivos, imposição de política, acompanhamento e até mesma implantação de código nos dispositivos em *borda*. A borda refere-se aos dispositivos, como sensores e atuadores que estão conectados ao, mas não uma Active Directory faz parte da Internet.

>[!div class="step-by-step"]
>[Anterior](architecture-approaches.md)
>[Próximo](serverless-architecture-considerations.md)