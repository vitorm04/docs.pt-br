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
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="d3ec8-102">Gerando classes de tipo de dados por meio de XML</span><span class="sxs-lookup"><span data-stu-id="d3ec8-102">Generating Data Type Classes from XML</span></span>
<span data-ttu-id="d3ec8-103">O .NET Framework 4,5 inclui um novo recurso para gerar classes de tipo de dados do XML.</span><span class="sxs-lookup"><span data-stu-id="d3ec8-103">.NET Framework 4.5 includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="d3ec8-104">Este tópico descreve como gerar automaticamente tipos de dados para o RSS feed do blog do .NET.</span><span class="sxs-lookup"><span data-stu-id="d3ec8-104">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="d3ec8-105">Obtendo o XML do feed RSS do blog do .NET</span><span class="sxs-lookup"><span data-stu-id="d3ec8-105">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1. <span data-ttu-id="d3ec8-106">No Internet Explorer, navegue até o [RSS feed do blog do .net](https://devblogs.microsoft.com/dotnet/feed/).</span><span class="sxs-lookup"><span data-stu-id="d3ec8-106">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://devblogs.microsoft.com/dotnet/feed/).</span></span>  
  
2. <span data-ttu-id="d3ec8-107">Clique com o botão direito do mouse na página e selecione **Exibir origem**.</span><span class="sxs-lookup"><span data-stu-id="d3ec8-107">Right-click the page and select **View Source**.</span></span>  
  
3. <span data-ttu-id="d3ec8-108">Copie o texto do feed pressionando **Ctrl + a** para selecionar todo o texto e **Ctrl + C** para copiar.</span><span class="sxs-lookup"><span data-stu-id="d3ec8-108">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="d3ec8-109">Criando os tipos de dados</span><span class="sxs-lookup"><span data-stu-id="d3ec8-109">Creating the data types</span></span>  
  
1. <span data-ttu-id="d3ec8-110">Abra um arquivo de código no qual o proxy deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="d3ec8-110">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="d3ec8-111">Esse arquivo deve fazer parte de um projeto .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="d3ec8-111">This file should be part of a .NET Framework 4.5 project.</span></span>  
  
2. <span data-ttu-id="d3ec8-112">Coloque o cursor em um local no arquivo fora de qualquer classe existente.</span><span class="sxs-lookup"><span data-stu-id="d3ec8-112">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3. <span data-ttu-id="d3ec8-113">Selecione **Editar**, **colar especial**e **colar XML como classes**.</span><span class="sxs-lookup"><span data-stu-id="d3ec8-113">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4. <span data-ttu-id="d3ec8-114">Classes chamadas `link`, `rss`, `rssChannel`, `rssChannelImage` esão`rssChannelItemGuid` criadas com os membros necessários para acessar os elementos no RSS feed. `rssChannelItem`</span><span class="sxs-lookup"><span data-stu-id="d3ec8-114">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="d3ec8-115">Usando as classes geradas</span><span class="sxs-lookup"><span data-stu-id="d3ec8-115">Using the generated classes</span></span>  
  
1. <span data-ttu-id="d3ec8-116">Depois que as classes são geradas, elas podem ser usadas em código como qualquer outra classe.</span><span class="sxs-lookup"><span data-stu-id="d3ec8-116">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="d3ec8-117">O exemplo de código a seguir retorna uma nova instância `rssChannelImage` da classe.</span><span class="sxs-lookup"><span data-stu-id="d3ec8-117">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```csharp  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
