---
title: Gerando classes de tipo de dados por meio de XML
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: bf5596211e78842153b7406273626a7fa3c3aeea
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990282"
---
# <a name="generating-data-type-classes-from-xml"></a>Gerando classes de tipo de dados por meio de XML
O .NET Framework 4,5 inclui um novo recurso para gerar classes de tipo de dados do XML. Este tópico descreve como gerar automaticamente tipos de dados para o RSS feed do blog do .NET.  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>Obtendo o XML do feed RSS do blog do .NET  
  
1. No Internet Explorer, navegue até o [RSS feed do blog do .net](https://devblogs.microsoft.com/dotnet/feed/).  
  
2. Clique com o botão direito do mouse na página e selecione **Exibir origem**.  
  
3. Copie o texto do feed pressionando **Ctrl + a** para selecionar todo o texto e **Ctrl + C** para copiar.  
  
### <a name="creating-the-data-types"></a>Criando os tipos de dados  
  
1. Abra um arquivo de código no qual o proxy deve ser usado. Esse arquivo deve fazer parte de um projeto .NET Framework 4,5.  
  
2. Coloque o cursor em um local no arquivo fora de qualquer classe existente.  
  
3. Selecione **Editar**, **colar especial**e **colar XML como classes**.  
  
4. Classes chamadas `link`, `rss`, `rssChannel`, `rssChannelImage` esão`rssChannelItemGuid` criadas com os membros necessários para acessar os elementos no RSS feed. `rssChannelItem`  
  
### <a name="using-the-generated-classes"></a>Usando as classes geradas  
  
1. Depois que as classes são geradas, elas podem ser usadas em código como qualquer outra classe. O exemplo de código a seguir retorna uma nova instância `rssChannelImage` da classe.  
  
    ```csharp  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
