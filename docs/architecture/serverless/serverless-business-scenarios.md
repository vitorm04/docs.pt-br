---
title: Cenários de negócios de exemplo e casos de uso para aplicativos sem servidor
description: Aprenda sem servidor com uma abordagem prática acessando exemplos que variam desde o processamento de imagens até back-ends móveis e pipelines de ETL.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 8a2301b3c7a5f4a1f465677f31371d5b94783692
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2019
ms.locfileid: "72522394"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>Casos de uso e cenários de negócios sem servidor

Há muitos casos de uso e cenários para aplicativos sem servidor. Este capítulo inclui exemplos que ilustram os diferentes cenários. Os cenários incluem links para documentação relacionada e repositórios de código-fonte público. Os exemplos neste capítulo permitem que você comece a usar sua própria compilação e implementação de soluções sem servidor.

## <a name="analyze-and-archive-images"></a>Analisar e arquivar imagens

Este exemplo demonstra eventos sem servidor (grade de eventos), fluxos de trabalho (aplicativo lógico) e código (Azure Functions). Ele também mostra como integrar com outro recurso, neste caso, serviços cognitivas para análise de imagem.

Um aplicativo de console permite passar um link para uma URL na Web. O aplicativo publica a URL como uma mensagem de grade de eventos. Em paralelo, um aplicativo de funções sem servidor e um aplicativo lógico assinam a mensagem. O aplicativo de funções sem servidor serializa a imagem no armazenamento de BLOBs. Ele também armazena informações no armazenamento de tabelas do Azure. Os metadados armazenam a URL da imagem original e o nome da imagem de BLOB. O aplicativo lógico interage com a API do Visão Personalizada para analisar a imagem e criar uma legenda gerada pelo computador. A legenda é armazenada na tabela de metadados.

![Analisar e arquivar a arquitetura de imagens](./media/image-processing-example.png)

Um SPA (aplicativo de página única) separado chama uma função sem servidor para obter uma lista de imagens e metadados. Para cada imagem, ele chama outra função que entrega os dados de imagem do arquivo morto. O resultado final é uma galeria com legendas automáticas.

![Galeria de imagens automatizada](./media/automated-image-gallery.png)

O repositório completo e as instruções para criar o aplicativo lógico estão disponíveis aqui: [cola de grade de eventos](https://github.com/JeremyLikness/Event-Grid-Glue).

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a>Cliente móvel de plataforma cruzada usando Xamarin. Forms e funções

Veja como implementar uma função simples sem servidor do Azure no portal da Web do Azure ou no Visual Studio. Crie um cliente com o Xamarin. Forms que é executado em Android, iOS e Windows. O aplicativo é então refinado para usar JavaScript Object Notation (JSON) como uma mídia de comunicação entre o servidor e os clientes móveis com um back-end sem servidor.

Para obter mais informações, consulte [implementando uma função simples do Azure com um cliente Xamarin. Forms](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/).

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a>Gerar um mosaico de fotos com reconhecimento de imagem sem servidor

O exemplo usa Azure Functions e serviços cognitivas da Microsoft Serviço de Visão Personalizada para gerar um mosaico de fotos a partir de uma imagem de entrada. O modelo é treinado para reconhecer imagens. Quando uma imagem é carregada, ela reconhece a imagem e pesquisa com o Bing. A imagem original é recomposta usando os resultados da pesquisa.

![Foto de olho de Orlando e mosaico](./media/orlando-eye-both.png)

Por exemplo, você pode treinar seu modelo com pontos de referência Orlando, como o olho de Orlando. Visão Personalizada reconhecerá uma imagem do olho de Orlando e a função criará um mosaico de fotos composto pelos resultados da pesquisa de imagem do Bing para "olho de Orlando".

Para obter mais informações, consulte [Azure Functions o gerador de mosaico de fotos](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/).

## <a name="migrate-an-existing-application-to-the-cloud"></a>Migrar um aplicativo existente para a nuvem

Conforme discutido nos capítulos anteriores, é comum adotar uma arquitetura de N camadas para hospedar seu aplicativo local. Embora a migração de recursos "no estado em que se encontra" usando máquinas virtuais seja o caminho menos arriscado para a nuvem, muitas empresas optam por usar a oportunidade de refatorar seus aplicativos. Felizmente, a refatoração não precisa ser um esforço "tudo ou nada". Na verdade, é possível migrar seu aplicativo e, em seguida, substituir componentes por contrapartes nativas da nuvem.

O aplicativo usa o recurso de proxies do Azure Functions para habilitar a refatoração de um ponto de extremidade do código local herdado para um ponto de extremidade sem servidor.

![Arquitetura de migração](./media/migration-architecture.png)

O proxy fornece um único ponto de extremidade de API que é atualizado para redirecionar solicitações individuais à medida que elas são movidas para funções sem servidor.

Você pode exibir um vídeo que percorre toda a migração: comparando [e Shift com o Azure Functions sem servidor](https://channel9.msdn.com/Events/Connect/2017/E102). Acesse o código de exemplo: [traga seu próprio aplicativo](https://github.com/JeremyLikness/bring-own-app-connect-17).

## <a name="parse-a-csv-file-and-insert-into-a-database"></a>Analisar um arquivo CSV e inseri-lo em um banco de dados

Extração, transformação e carregamento (ETL) é uma função comercial comum que integra sistemas diferentes. As abordagens tradicionais geralmente envolvem a configuração de servidores FTP dedicados e, em seguida, a implantação de trabalhos agendados para analisar arquivos e traduzi-los para uso comercial. A arquitetura sem servidor facilita o trabalho, pois um gatilho pode ser acionado quando o arquivo é carregado. Azure Functions resolve tarefas como ETL por meio de sua composição ideal de pequenas partes de código que se concentram em um problema específico.

![Captura de tela que mostra o processo de análise de CSV.](./media/serverless-business-scenarios/csv-parse-database-import.png)

Para o código-fonte e um laboratório prático, consulte [laboratório de importação de CSV](https://github.com/JeremyLikness/azure-fn-file-process-hol).

## <a name="shorten-links-and-track-metrics"></a>Encurtar links e controlar métricas

As ferramentas de redução de links ajudaram originalmente a codificar URLs em postagens curtas no Twitter para acomodar o limite de 140 caracteres. Eles cresceram para abranger vários usos, mais comumente para controlar o clique para análise. O link Shortener Scenario é um aplicativo totalmente sem servidor que gerencia as métricas de links e relatórios.

Azure Functions é usado para servir um aplicativo de página única (SPA) que permite colar a URL longa e gerar URLs curtas. As URLs são marcadas para controlar coisas como campanhas (tópicos) e meios (como redes sociais nas quais os links são postados). O código curto é armazenado no armazenamento de tabelas do Azure como a chave, com a URL longa como o valor. Quando você clica no link curto, outra função pesquisa a URL longa, envia um redirecionamento e coloca as informações sobre o evento em uma fila. Outra função do Azure processa a fila e coloca as informações em Azure Cosmos DB.

![Vincular arquitetura do Shortener](./media/link-shortener-architecture.png)

Em seguida, você pode criar um painel de Power BI para coletar informações sobre os dados coletados. No back-end, Application Insights fornece métricas importantes. A telemetria inclui quanto tempo leva para o usuário médio redirecionar e quanto tempo leva para acessar o armazenamento de tabelas do Azure.

![Exemplo de Power BI](./media/power-bi-example.png)

O repositório Shortener de link completo com instruções está disponível aqui: [URL sem servidor Shortener](https://github.com/jeremylikness/serverless-url-shortener). Você pode ler sobre uma versão simplificada aqui: [armazenamento do Azure para aplicativos .NET sem servidor em minutos](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/).

## <a name="verify-device-connectivity-using-a-ping"></a>Verificar a conectividade do dispositivo usando um ping

O exemplo consiste em um hub IoT do Azure e uma função do Azure. Uma nova mensagem no Hub IoT dispara a função do Azure. O código sem servidor envia o mesmo conteúdo de mensagem de volta para o dispositivo que o enviou. O projeto tem todo o código e a configuração de implantação necessários para a solução.

Para obter mais informações, consulte [ping do Hub IOT do Azure](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/).

## <a name="recommended-resources"></a>Recursos recomendados

- [Gerador de mosaico de fotos Azure Functions](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)
- [Ping do Hub IoT do Azure](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)
- [Armazenamento do Azure para aplicativos .NET sem servidor em minutos](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/)
- [Traga seu próprio aplicativo](https://github.com/JeremyLikness/bring-own-app-connect-17)
- [Laboratório de importação de CSV](https://github.com/JeremyLikness/azure-fn-file-process-hol)
- [Cola de grade de eventos](https://github.com/JeremyLikness/Event-Grid-Glue)
- [Implementando uma função simples do Azure com um cliente Xamarin. Forms](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)
- [Migrar e Shift com o Azure Functions sem servidor](https://channel9.msdn.com/Events/Connect/2017/E102)
- [URL sem servidor Shortener](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
>[Anterior](orchestration-patterns.md)
>[Próximo](serverless-conclusion.md)
