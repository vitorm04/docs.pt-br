---
title: Gerando classes de tipo de dados por meio de XML
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: c1b5dfda8aa5370dbc202ab90c75ab5677970467
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929565"
---
# <a name="generating-data-type-classes-from-xml"></a>Gerando classes de tipo de dados por meio de XML
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] inclui um novo recurso para gerar classes de tipo de dados de XML. Este tópico descreve como gerar automaticamente os tipos de dados para .NET Blog RSS feed.  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>Como obter o XML do .NET Blog RSS feed  
  
1. No Internet Explorer, navegue até a [feed RSS do Blog de .NET](https://devblogs.microsoft.com/dotnet/feed/).  
  
2. A página com o botão direito e selecione **Exibir código-fonte**.  
  
3. Copie o texto do feed pressionando **Ctrl + T** para selecionar todo o texto, e **Ctrl + C** para copiar.  
  
### <a name="creating-the-data-types"></a>Criar os tipos de dados  
  
1. Abra um arquivo de código em que o proxy deve ser usado. Esse arquivo deve ser parte de um [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] projeto.  
  
2. Coloque o cursor em um local no arquivo fora de qualquer classe existente.  
  
3. Selecione **edite**, **Colar especial**, **colar XML como Classes**.  
  
4. Classes chamadas `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` e `rssChannelItemGuid` são criados com os membros necessários para acessar os elementos no RSS feed.  
  
### <a name="using-the-generated-classes"></a>Usando as classes geradas  
  
1. Depois que as classes são geradas, pode ser usados no código como quaisquer outras classes. O exemplo de código a seguir retorna uma nova instância do `rssChannelImage` classe.  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
