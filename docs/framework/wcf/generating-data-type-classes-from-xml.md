---
title: Gerando classes de tipo de dados por meio de XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 67b9e239c8b60511caf3989c0b3a1a5d6dcc9b26
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="generating-data-type-classes-from-xml"></a>Gerando classes de tipo de dados por meio de XML
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]inclui um novo recurso para gerar classes de tipo de dados de XML. Este tópico descreve como gerar automaticamente os tipos de dados para o .NET Blog o RSS feed.  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>Obter o XML do .NET Blog RSS feed  
  
1.  No Internet Explorer, navegue até o [.NET Blog RSS feed](https://blogs.msdn.microsoft.com/dotnet/feed/).  
  
2.  A página e selecione **Exibir código-fonte**.  
  
3.  Copie o texto do feed pressionando **Ctrl + A** para selecionar todo o texto, e **Ctrl + C** para copiar.  
  
### <a name="creating-the-data-types"></a>Criar os tipos de dados  
  
1.  Abra um arquivo de código em que o proxy será usado. Esse arquivo deve ser parte de um [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] projeto.  
  
2.  Posicione o cursor em um local no arquivo fora de todas as classes existentes.  
  
3.  Selecione **editar**, **Colar especial**, **colar XML como Classes**.  
  
4.  Classes chamadas `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` e `rssChannelItemGuid` são criados com os membros necessários para acessar os elementos no RSS feed.  
  
### <a name="using-the-generated-classes"></a>Usando as classes geradas  
  
1.  Depois que as classes são geradas, eles podem ser usados em código como quaisquer outras classes. O exemplo de código a seguir retorna uma nova instância do `rssChannelImage` classe.  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
