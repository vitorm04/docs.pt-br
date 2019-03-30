---
title: Exemplos de cenários de negócios e casos de uso para aplicativos sem servidor
description: Saiba mais sem servidor com uma abordagem prática acessando amostras de intervalo de processamento de imagens para o back-ends móveis e os pipelines ETL.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 177fb1d7f79a0067ab185e520778b593d4b8eaf6
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653893"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>Casos de uso e cenários de negócios sem servidor

Há muitos casos de uso e cenários para aplicativos sem servidor. Este capítulo inclui exemplos que ilustram os diferentes cenários. Os cenários incluem links para documentação relacionada e repositórios de código do código-fonte público. Os exemplos neste capítulo permitem que você começar a usar por conta própria criando e implementando soluções sem servidor.

## <a name="analyze-and-archive-images"></a>Analisar e arquivamento de imagens

Este exemplo demonstra o código (Azure Functions), os fluxos de trabalho (lógica de aplicativo) e eventos sem servidor (grade de eventos). Ele também mostra como integrar com outro recurso, neste caso os serviços Cognitivos para análise de imagem.

Um aplicativo de console permite que você passe um link para uma URL na web. O aplicativo publica a URL como uma mensagem de grade de eventos. Em paralelo, um aplicativo de funções sem servidor e um aplicativo lógico assinem a mensagem. O aplicativo de funções sem servidor serializa a imagem no armazenamento de BLOBs. Ele também armazena informações no armazenamento de tabelas do Azure. Os metadados armazenam a URL da imagem original e o nome da imagem do blob. O aplicativo lógico interage com a API de visão personalizada para analisar a imagem e criar uma legenda gerado pelo computador. A legenda é armazenada na tabela de metadados.

![Analise e arquive a arquitetura de imagens](./media/image-processing-example.png)

Um aplicativo separado de página única (SPA) chama uma função sem servidor para obter uma lista de imagens e metadados. Para cada imagem, ele chama outra função que fornece os dados de imagem do arquivo morto. O resultado final é uma galeria com legendas automáticas.

![Galeria de imagens automatizado](./media/automated-image-gallery.png)

O repositório completo e instruções para criar o aplicativo lógico estão disponíveis aqui: [Cola de grade de eventos](https://github.com/JeremyLikness/Event-Grid-Glue).

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a>Cliente móvel de plataforma cruzada usando xamarin. Forms e funções

Veja como implementar uma função do Azure sem servidor simples no Portal da Web do Azure ou no Visual Studio. Crie um cliente com o xamarin. Forms que é executado no Windows, iOS e Android. O aplicativo está aprimorado, em seguida, para usar a notação JSON (JavaScript Object) como um meio de comunicação entre o servidor e os clientes móveis com um back-end sem servidor.

Para obter mais informações, consulte [implementando uma função do Azure simples com um cliente xamarin. Forms](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a>Gerar um mosaico de foto com reconhecimento de imagem sem servidor

O exemplo usa o Azure Functions e o Microsoft Cognitive Services serviço personalizado de visão para gerar um mosaico de foto de uma imagem de entrada. O modelo é treinado para reconhecer imagens. Quando uma imagem é carregada, ele reconhece a imagem e pesquisa com o Bing. A imagem original é recomposta usando os resultados da pesquisa.

![Mosaico e foto de olho Orlando](./media/orlando-eye-both.png)

Por exemplo, você pode treinar o modelo com pontos de referência Orlando, como o olho Orlando. Visão personalizada reconhecerá que uma imagem do olho Orlando, e a função criará um mosaico de foto composto de resultados da pesquisa de imagem do Bing para "Orlando olhos".

Para obter mais informações, consulte [gerador de mosaico de foto do Azure Functions](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/).

## <a name="migrate-an-existing-application-to-the-cloud"></a>Migrar um aplicativo existente para a nuvem

Conforme discutido nos capítulos anteriores, é comum para adotar uma arquitetura de N camadas para hospedar seu aplicativo no local. Embora a migração de recursos "como está" usando as máquinas virtuais é o caminho menos arriscado para a nuvem, muitas empresas optam por usar a oportunidade para refatorar seus aplicativos. Felizmente, refatoração não precisa ser um esforço "tudo ou nada". Na verdade, é possível migrar seu aplicativo, em seguida, gradativamente substituir componentes com equivalentes nativos de nuvem.

O aplicativo usa o recurso de proxies do Azure Functions para permitir a refatoração de um ponto de extremidade do código herdado no local para um ponto de extremidade sem servidor.

![Arquitetura de migração](./media/migration-architecture.png)

O proxy fornece um ponto de extremidade de API único que é atualizado para redirecionar solicitações individuais conforme eles são movidos para funções sem servidor.

Você pode exibir um vídeo que orienta durante a migração inteira: [Lift- and -shift com o Azure functions sem servidor](https://channel9.msdn.com/Events/Connect/2017/E102). Acesse o código de exemplo: [Traga seu próprio aplicativo](https://github.com/JeremyLikness/bring-own-app-connect-17).

## <a name="parse-a-csv-file-and-insert-into-a-database"></a>Analisar um arquivo CSV e inserir em um banco de dados

Extração, transformação e carregamento (ETL) é uma função de negócios comuns que se integra sistemas diferentes. As abordagens tradicionais frequentemente envolvem a configuração de servidores dedicados do FTP e em seguida, implantando trabalhos agendados para analisar arquivos e convertê-las para uso comercial. Arquitetura sem servidor facilita o trabalho porque um gatilho ser acionado quando o arquivo é carregado. Tarefas de pesca funções do Azure, como ETL através de sua composição ideal de pequenos trechos de código que se concentram em um problema específico.

![Captura de tela que mostra o processo de análise de csv.](./media/serverless-business-scenarios/csv-parse-database-import.png)

Para código-fonte e um laboratório prático, consulte [importação de CSV laboratório](https://github.com/JeremyLikness/azure-fn-file-process-hol).

## <a name="shorten-links-and-track-metrics"></a>Reduza os links e controlar as métricas

Ferramentas de encurtar link originalmente ajudou a codificar URLs resumindo twitter postagens para acomodar o limite de 140 caracteres. Eles já expandido para englobar vários usos, mais comumente para acompanhar clickthroughs para análise. O cenário de shortener de link é um aplicativo totalmente sem servidor que gerencia os links e relata as métricas.

O Azure Functions é usado para atender a um aplicativo de página única (SPA) que permite que você cole a URL longa e gerar URLs curtas. As URLs são marcadas para controlar coisas como campanhas (tópicos) e mídias (como redes sociais que os links são postados). O código curto é armazenado no armazenamento de tabelas do Azure como a chave, com a URL longa como o valor. Quando você clica no link curto, outra função procura a URL longa, envia um redirecionamento e coloca informações sobre o evento em uma fila. Outra função do Azure processa a fila e coloca as informações para o Azure Cosmos DB.

![Arquitetura de shortener de link](./media/link-shortener-architecture.png)

Em seguida, você pode criar um painel do Power BI para reunir informações sobre os dados coletados. No back-end, o Application Insights fornece métricas importantes. Telemetria inclui quanto tempo demora para o usuário médio redirecionar e quanto tempo demora para acessar o armazenamento de tabela do Azure.

![Exemplo do Power BI](./media/power-bi-example.png)

O repositório de shortener link completo com instruções está disponível aqui: [Serverless URL shortener](https://github.com/jeremylikness/serverless-url-shortener). Você pode ler sobre uma versão simplificada aqui: [Armazenamento do Azure para aplicativos .NET sem servidor em questão de minutos](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/).

## <a name="verify-device-connectivity-using-a-ping"></a>Verificar a conectividade do dispositivo usando um ping

O exemplo consiste em um Hub de IoT do Azure e uma função do Azure. Uma nova mensagem no IoT Hub dispara a função do Azure. O código sem servidor envia a mesma mensagem de conteúdo para o dispositivo que o enviou. O projeto tem toda a configuração de implantação e o código necessária para a solução.

Para obter mais informações, consulte [ping do IoT Hub do Azure](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/).

## <a name="recommended-resources"></a>Recursos recomendados

* [Gerador de mosaico de foto de funções do Azure](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)
* [Ping de IoT Hub do Azure](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)
* [Armazenamento do Azure para aplicativos .NET sem servidor em questão de minutos](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/)
* [Traga seu próprio aplicativo](https://github.com/JeremyLikness/bring-own-app-connect-17)
* [Laboratório de importação CSV](https://github.com/JeremyLikness/azure-fn-file-process-hol)
* [Cola de grade de eventos](https://github.com/JeremyLikness/Event-Grid-Glue)
* [Implementando uma função do Azure simples com um cliente xamarin. Forms](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)
* [Lift- and -shift com o Azure functions sem servidor](https://channel9.msdn.com/Events/Connect/2017/E102)
* [Serverless URL shortener](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
>[Anterior](orchestration-patterns.md)
>[Próximo](serverless-conclusion.md)