---
title: Amostrar cenários de negócios e usar casos para aplicativos sem servidor
description: Aprenda sem servidor com uma abordagem prática acessando amostras que vão desde o processamento de imagens até back ends móveis e pipelines ETL.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 5f0d7a4c5cd736d1168ec76c1c0ea19627505f15
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76787887"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>Casos de uso e cenários de negócios sem servidor

Existem muitos casos de uso e cenários para aplicativos sem servidor. Este capítulo inclui amostras que ilustram os diferentes cenários. Os cenários incluem links para documentação relacionada e repositórios de código-fonte público. As amostras deste capítulo permitem que você comece em seu próprio edifício e implemente soluções sem servidor.

## <a name="analyze-and-archive-images"></a>Analisar e arquivar imagens

Esta amostra demonstra eventos sem servidor (Event Grid), fluxos de trabalho (Logic App) e código (Funções Azure). Também mostra como se integrar com outro recurso, neste caso serviços cognitivos para análise de imagem.

Um aplicativo de console permite que você passe um link para uma URL na Web. O aplicativo publica a URL como uma mensagem de grade de eventos. Paralelamente, um aplicativo de função sem servidor e um aplicativo lógico assinam a mensagem. O aplicativo de função sem servidor serializa a imagem para o armazenamento blob. Ele também armazena informações no Azure Table Storage. Os metadados armazenam a URL de imagem original e o nome da imagem blob. O aplicativo lógico interage com a API de visão personalizada para analisar a imagem e criar uma legenda gerada por máquina. A legenda é armazenada na tabela de metadados.

![Analisar e arquivar a arquitetura de imagens](./media/image-processing-example.png)

Um aplicativo de página única separado (SPA) chama uma função sem servidor para obter uma lista de imagens e metadados. Para cada imagem, ela chama outra função que fornece os dados de imagem do arquivo. O resultado final é uma galeria com legendas automáticas.

![Galeria de imagens automatizada](./media/automated-image-gallery.png)

O repositório completo e as instruções para construir o aplicativo lógico estão disponíveis aqui: [Cola da grade de eventos](https://github.com/JeremyLikness/Event-Grid-Glue).

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a>Cliente móvel multiplataforma usando Xamarin.Forms e funções

Veja como implementar uma simples função Azure sem servidor no Portal Web do Azure ou no Visual Studio. Crie um cliente com Xamarin.Forms que seja executado no Android, iOS e Windows. O aplicativo é então refinado para usar A notação de objeto JavaScript (JSON) como um meio de comunicação entre o servidor e os clientes móveis com um back-end sem servidor.

Para obter mais informações, consulte [Implementando uma função azure simples com um cliente Xamarin.Forms](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/).

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a>Gerar um mosaico de fotos com reconhecimento de imagem sem servidor

A amostra usa funções do Azure e do Serviço de Visão Personalizada do Microsoft Cognitive Services para gerar um mosaico fotográfico a partir de uma imagem de entrada. O modelo é treinado para reconhecer imagens. Quando uma imagem é carregada, ela reconhece a imagem e pesquisa com Bing. A imagem original é recomposta usando os resultados da pesquisa.

![Foto de olho de Orlando e mosaico](./media/orlando-eye-both.png)

Por exemplo, você pode treinar seu modelo com pontos turísticos de Orlando, como o Orlando Eye. A Custom Vision reconhecerá uma imagem do Orlando Eye, e a função criará um mosaico fotográfico composto pelos resultados de pesquisa de imagem de Bing para "Orlando Eye".

Para obter mais informações, consulte [o gerador de mosaico de fotos Azure Functions](https://github.com/Azure-Samples/functions-dotnet-photo-mosaic).

## <a name="migrate-an-existing-application-to-the-cloud"></a>Migrar um aplicativo existente para a nuvem

Como discutido em capítulos anteriores, é comum adotar uma arquitetura N-Tier para hospedar seu aplicativo no local. Embora migrar recursos "como é" usando máquinas virtuais seja o caminho menos arriscado para a nuvem, muitas empresas optam por usar a oportunidade para refatorar suas aplicações. Felizmente, refatorar não precisa ser um esforço "tudo ou nada". Na verdade, é possível migrar seu aplicativo e substituir componentes por contrapartes nativas da nuvem.

O aplicativo usa o recurso proxies do Azure Functions para permitir a refatoração de um ponto final do código local legado para um ponto final sem servidor.

![Arquitetura de migração](./media/migration-architecture.png)

O proxy fornece um único ponto final de API que é atualizado para redirecionar solicitações individuais à medida que são movidas para funções sem servidor.

Você pode ver um vídeo que percorre toda a migração: [Levantar e shift com funções azure sem servidor](https://channel9.msdn.com/Events/Connect/2017/E102). Acesse o código de exemplo: [Traga seu próprio aplicativo](https://github.com/JeremyLikness/bring-own-app-connect-17).

## <a name="parse-a-csv-file-and-insert-into-a-database"></a>Analise um arquivo CSV e insira em um banco de dados

Extrair, Transformar e Carregar (ETL) é uma função de negócios comum que integra diferentes sistemas. As abordagens tradicionais geralmente envolvem a criação de servidores FTP dedicados e, em seguida, a implantação de trabalhos programados para analisar arquivos e traduzi-los para uso comercial. A arquitetura sem servidor facilita o trabalho porque um gatilho pode ser acionado quando o arquivo é carregado. O Azure Functions aborda tarefas como o ETL através de sua composição ideal de pequenos pedaços de código que se concentram em um problema específico.

![Captura de tela que mostra o processo de análise csv.](./media/serverless-business-scenarios/csv-parse-database-import.png)

Para obter código fonte e um laboratório prático, consulte [o laboratório de importação csv](https://github.com/JeremyLikness/azure-fn-file-process-hol).

## <a name="shorten-links-and-track-metrics"></a>Encurtar links e rastrear métricas

Ferramentas de encurtamento de link originalmente ajudaram a codificar URLs em postagens curtas no Twitter para acomodar o limite de 140 caracteres. Eles cresceram para abranger vários usos, mais comumente para rastrear click-throughs para análises. O cenário de encurtamento de links é um aplicativo totalmente sem servidor que gerencia links e métricas de relatórios.

As funções do Azure são usadas para servir um Aplicativo de Página Única (SPA) que permite colar a URL longa e gerar URLs curtas. Os URLs são marcados para rastrear coisas como campanhas (tópicos) e meios (como redes sociais para as quais os links são postados). O código curto é armazenado no Azure Table Storage como a chave, com a URL longa como o valor. Quando você clica no link curto, outra função procura a URL longa, envia um redirecionamento e coloca informações sobre o evento em uma fila. Outra função do Azure processa a fila e coloca as informações no Azure Cosmos DB.

![Arquitetura de encurtador de link](./media/link-shortener-architecture.png)

Em seguida, você pode criar um painel power bi para coletar insights sobre os dados coletados. No back-end, o Application Insights fornece métricas importantes. A telemetria inclui quanto tempo leva para o usuário médio redirecionar e quanto tempo leva para acessar o Azure Table Storage.

![Exemplo de POWER BI](./media/power-bi-example.png)

O repositório completo do encurtador de link com instruções está disponível aqui: [encurtador de URL sem servidor](https://github.com/jeremylikness/serverless-url-shortener). Você pode ler sobre uma versão simplificada aqui: [Azure Storage para aplicativos .NET sem servidor em minutos](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/).

## <a name="verify-device-connectivity-using-a-ping"></a>Verifique a conectividade do dispositivo usando um ping

A amostra consiste em um Hub Azure IoT e uma função Azure. Uma nova mensagem no IoT Hub aciona a função Azure. O código sem servidor envia o mesmo conteúdo de mensagem de volta para o dispositivo que o enviou. O projeto tem toda a configuração de código e implantação necessária para a solução.

Para obter mais informações, consulte [o ping do Azure IoT Hub](https://github.com/Azure-Samples/iot-hub-node-ping).

## <a name="recommended-resources"></a>Recursos recomendados

- [Gerador de mosaico fotográfico azure Functions](https://github.com/Azure-Samples/functions-dotnet-photo-mosaic)
- [Ping no Hub do Azure IoT](https://github.com/Azure-Samples/iot-hub-node-ping)
- [Armazenamento do Azure para aplicativos .NET sem servidor em minutos](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/)
- [Traga seu próprio aplicativo](https://github.com/JeremyLikness/bring-own-app-connect-17)
- [Laboratório de importação csv](https://github.com/JeremyLikness/azure-fn-file-process-hol)
- [Cola da grade de eventos](https://github.com/JeremyLikness/Event-Grid-Glue)
- [Implementando uma função azure simples com um cliente Xamarin.Forms](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)
- [Levantar e shift com funções do Azure sem servidor](https://channel9.msdn.com/Events/Connect/2017/E102)
- [Encurtador de URL sem servidor](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
>[Próximo](orchestration-patterns.md)
>[anterior](serverless-conclusion.md)
