---
title: Gerando classes de tipo de dados por meio de XML
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: d66cbd1806b90d21a483d0c470f953ddfb9c4fca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184127"
---
# <a name="generating-data-type-classes-from-xml"></a>Gerando classes de tipo de dados por meio de XML
.NET Framework 4.5 inclui um novo recurso para gerar classes de tipo de dados a partir de XML. Este tópico descreve como gerar automaticamente tipos de dados para o feed .NET Blog RSS.  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>Obtendo o XML no feed .NET Blog RSS  
  
1. No Internet Explorer, navegue até o [feed RSS do Blog .NET](https://devblogs.microsoft.com/dotnet/feed/).  
  
2. Clique com o botão direito do mouse na página e **selecione 'Exibir origem '**.  
  
3. Copie o texto da alimentação pressionando **Ctrl+A** para selecionar todo o texto e **Ctrl+C** para copiar.  
  
### <a name="creating-the-data-types"></a>Criando os tipos de dados  
  
1. Abra um arquivo de código onde o proxy deve ser usado. Este arquivo deve fazer parte de um projeto .NET Framework 4.5.  
  
2. Coloque o cursor em um local no arquivo fora de qualquer classe existente.  
  
3. Selecione **Editar, Colar Especial,** **Colar XML como Classes**. **Edit**  
  
4. As `link`classes `rss` `rssChannel`chamadas `rssChannelImage` `rssChannelItem` , `rssChannelItemGuid` , , e são criadas com os membros necessários para acessar os elementos no feed RSS.  
  
### <a name="using-the-generated-classes"></a>Usando as classes geradas  
  
1. Uma vez que as classes são geradas, elas podem ser usadas em código como qualquer outra classe. O exemplo de código a `rssChannelImage` seguir retorna uma nova instância da classe.  
  
    ```csharp
    var channelImage = new rssChannelImage()
    {
        title = "MyImage",
        link = "http://www.contoso.com/images/channelImage.jpg",
        url = "http://www.contoso.com/entries/myEntry.html"
    };  
    ```
