---
title: Arquitetura sem servidor - Aplicativos sem servidor
description: Exploração de várias arquiteturas e aplicativos que são suportados por arquiteturas sem servidor, incluindo aplicativos web, mobile e IoT.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 838dcd7b41df0d8297e1ae10f9c04a8d5b83b332
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522398"
---
# <a name="serverless-architecture"></a>Arquitetura sem servidor

Existem muitas abordagens para usar arquiteturas [sem servidor.](https://azure.com/serverless) Este capítulo explora exemplos de arquiteturas comuns que integram sem servidor. Também abrange preocupações que podem representar desafios adicionais ou exigir consideração extra ao implementar sem servidor. Finalmente, vários exemplos de design são fornecidos que ilustram vários casos de uso sem servidor.

Os hosts sem servidor geralmente usam uma camada de PaaS ou de contêiner existente para gerenciar as instâncias sem servidor. Por exemplo, as funções do Azure são baseadas no [Azure App Service](https://docs.microsoft.com/azure/app-service/). O Serviço de Aplicativo é usado para dimensionar instâncias e gerenciar o tempo de execução que executa o código Funções do Azure. Para funções baseadas no Windows, o host é executado como PaaS e dimensiona o tempo de execução .NET. Para funções baseadas em Linux, o host aproveita os contêineres.

![Arquitetura Funções do Azure](./media/azure-functions-architecture.png)

O WebJobs Core fornece um contexto de execução para a função. O Language Runtime executa scripts, executa bibliotecas e hospeda a estrutura para o idioma-alvo. Por exemplo, node.js é usado para executar funções JavaScript e o .NET Framework é usado para executar funções C#. Você aprenderá mais sobre opções de idioma e plataforma mais tarde neste capítulo.

Alguns projetos podem se beneficiar de uma abordagem "all-in" para sem servidor. Aplicativos que dependem fortemente de microsserviços podem implementar todos os microserviços usando tecnologia sem servidor. A maioria dos aplicativos são híbridos, seguindo um design n-tier e usando sem servidor para os componentes que fazem sentido porque os componentes são modulares e independentemente escaláveis. Para ajudar a entender esses cenários, esta seção passa por alguns exemplos de arquitetura comuns que usam sem servidor.

## <a name="full-serverless-back-end"></a>Back-end completo sem servidor

O back-end completo sem servidor é ideal para vários tipos de cenários, especialmente quando se constrói aplicativos novos ou "campo verde". Um aplicativo com uma grande área de superfície de APIs pode se beneficiar da implementação de cada API como uma função sem servidor. Aplicativos baseados na arquitetura de microsserviços são outro exemplo que pode ser implementado como um back-end completo sem servidor. Os microserviços se comunicam por vários protocolos entre si. Cenários específicos incluem:

- Produtos SaaS baseados em API (exemplo: processador de pagamentos financeiros).
- Aplicativos orientados por mensagem (exemplo: solução de monitoramento de dispositivos).
- Aplicativos focados na integração entre serviços (exemplo: aplicativo de reserva de companhias aéreas).
- Processos que são executados periodicamente (exemplo: limpeza de banco de dados baseada em temporizador).
- Aplicativos focados na transformação de dados (exemplo: importação desencadeada pelo upload de arquivos).
- Extrair processos de Transformação e Carga (ETL).

Existem outros casos de uso mais específicos que são abordados posteriormente neste documento.

## <a name="monoliths-and-starving-the-beast"></a>Monólitos e "faminto saquea-a-besta"

Um desafio comum é migrar uma aplicação monolítica existente para a nuvem. A abordagem menos arriscada é "levantar e mudar" inteiramente para máquinas virtuais. Muitas lojas preferem usar a migração como uma oportunidade para modernizar sua base de código. Uma abordagem prática para a migração é chamada de "fome da besta". Nesse cenário, o monólito é migrado "como está" para começar. Em seguida, os serviços selecionados são modernizados. Em alguns casos, a assinatura do serviço é idêntica à original: ele simplesmente é hospedado como uma função. Os clientes são atualizados para usar o novo serviço em vez do ponto final do monolito. Nesse ínterim, etapas como a replicação de banco de dados permitem que microsserviços hospedem seu próprio armazenamento mesmo quando as transações ainda são tratadas pelo monolito. Eventualmente, todos os clientes são migrados para os novos serviços. O monólito está "faminto" (seus serviços não são mais chamados) até que todas as funcionalidades foram substituídas. A combinação de sem servidor e proxies pode facilitar grande parte dessa migração.

![Migração de monólito sem servidor](./media/serverless-monolith-migration.png)

Para saber mais sobre essa abordagem, assista ao vídeo: [Traga seu aplicativo para a nuvem com funções azure sem servidor](https://channel9.msdn.com/Events/Connect/2017/E102).

## <a name="web-apps"></a>Aplicativos Web

Os aplicativos web são ótimos candidatos para aplicativos sem servidor. Existem duas abordagens comuns para aplicativos web hoje: orientada por servidor e orientada pelo cliente (como aplicativo de página única ou SPA). Os aplicativos web orientados pelo servidor normalmente usam uma camada de middleware para emitir chamadas de API para renderizar a Interface do Usuário da Web. Os aplicativos SPA fazem chamadas de API REST diretamente do navegador. Em ambos os cenários, o serverless pode acomodar a solicitação de middleware ou API REST, fornecendo a lógica de negócios necessária. Uma arquitetura comum é levantar um servidor web estático leve. O Aplicativo de Página Única (SPA) serve HTML, CSS, JavaScript e outros ativos do navegador. O aplicativo web então se conecta a um back-end de microsserviços.

## <a name="mobile-back-ends"></a>Extremidades traseiras móveis

O paradigma orientado por eventos de aplicativos sem servidor os torna ideais como back-ends móveis. O dispositivo móvel aciona os eventos e o código sem servidor é executado para satisfazer as solicitações. Aproveitar um modelo sem servidor permite que os desenvolvedores aprimorem a lógica de negócios sem ter que implantar uma atualização completa do aplicativo. A abordagem sem servidor também permite que as equipes compartilhem pontos finais e trabalhem em paralelo.

Os desenvolvedores móveis podem construir a lógica de negócios sem se tornarem especialistas no lado do servidor. Tradicionalmente, aplicativos móveis conectados a serviços locais. A construção da camada de serviço exigia a compreensão da plataforma do servidor e o paradigma de programação. Os desenvolvedores trabalharam com operações para provisionar servidores e configurá-los adequadamente. Às vezes, dias ou até semanas eram gastos na construção de um oleoduto de implantação. Todos esses desafios são enfrentados por sem servidor.

Sem servidor, o Serverless abstrai as dependências do lado do servidor e permite que o desenvolvedor se concentre na lógica de negócios. Por exemplo, um desenvolvedor móvel que constrói aplicativos usando uma estrutura JavaScript pode construir funções sem servidor com JavaScript também. O host sem servidor gerencia o sistema operacional, uma instância Node.js para hospedar o código, as dependências do pacote e muito mais. O desenvolvedor é fornecido um conjunto simples de entradas e um modelo padrão para saídas. Eles então podem se concentrar em construir e testar a lógica do negócio. Eles são, portanto, capazes de usar as habilidades existentes para construir a lógica back-end para o aplicativo móvel sem ter que aprender novas plataformas ou se tornar um "desenvolvedor do lado do servidor".

![Back-end móvel sem servidor](./media/serverless-mobile-backend.png)

A maioria dos provedores de nuvem oferece produtos sem servidor baseados em dispositivos móveis que simplificam todo o ciclo de vida do desenvolvimento móvel. Os produtos podem automatizar o provisionamento de bancos de dados para persistir dados, lidar com preocupações do DevOps, fornecer compilações baseadas em nuvem e estruturas de teste e a capacidade de roteirizar processos de negócios usando a linguagem preferida do desenvolvedor. Seguir uma abordagem sem servidor centrada no celular pode agilizar o processo. O Serverless remove a tremenda sobrecarga de provisionamento, configuração e manutenção de servidores para o back-end móvel.

## <a name="internet-of-things-iot"></a>Internet das coisas (IoT)

IoT refere-se a objetos físicos que são em rede. Às vezes são chamados de "dispositivos conectados" ou "dispositivos inteligentes". Tudo, desde carros e máquinas automáticas, pode ser conectado e enviar informações que vão desde o inventário até dados de sensores, como temperatura e umidade. Na empresa, a IoT oferece melhorias nos processos de negócios por meio de monitoramento e automação. Os dados de IoT podem ser usados para regular o clima em um grande armazém ou rastrear o inventário através da cadeia de suprimentos. IoT pode sentir derramamentos químicos e chamar os bombeiros quando a fumaça é detectada.

O grande volume de dispositivos e informações muitas vezes dita uma arquitetura orientada a eventos para direcionar e processar mensagens. Serverless é uma solução ideal por várias razões:

- Permite a escala à medida que o volume de dispositivos e dados aumenta.
- Acomoda a adição de novos pontos finais para suportar novos dispositivos e sensores.
- Facilita a versão independente para que os desenvolvedores possam atualizar a lógica de negócios para um dispositivo específico sem ter que implantar todo o sistema.
- Resiliência e menos tempo de inatividade.

A disseminação da IoT resultou em vários produtos sem servidor que se concentram especificamente em preocupações com IoT, como [o Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub). O Serverless automatiza tarefas como registro de dispositivos, aplicação de políticas, rastreamento e até mesmo implantação de código para dispositivos *na borda*. A borda refere-se a dispositivos como sensores e atuadores que estão conectados, mas não uma parte ativa da Internet.

>[!div class="step-by-step"]
>[Próximo](architecture-approaches.md)
>[anterior](serverless-architecture-considerations.md)
