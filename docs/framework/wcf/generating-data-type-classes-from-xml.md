---
title: Gerando classes de tipo de dados por meio de XML
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: b99bb40105398dbd91b910c4a19828d069c3d9e7
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380214"
---
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="2099f-102">Gerando classes de tipo de dados por meio de XML</span><span class="sxs-lookup"><span data-stu-id="2099f-102">Generating Data Type Classes from XML</span></span>
<span data-ttu-id="2099f-103">.NET framework 4.5 inclui um novo recurso para gerar classes de tipo de dados de XML.</span><span class="sxs-lookup"><span data-stu-id="2099f-103">.NET Framework 4.5 includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="2099f-104">Este tópico descreve como gerar automaticamente os tipos de dados para .NET Blog RSS feed.</span><span class="sxs-lookup"><span data-stu-id="2099f-104">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="2099f-105">Como obter o XML do .NET Blog RSS feed</span><span class="sxs-lookup"><span data-stu-id="2099f-105">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1. <span data-ttu-id="2099f-106">No Internet Explorer, navegue até a [feed RSS do Blog de .NET](https://devblogs.microsoft.com/dotnet/feed/).</span><span class="sxs-lookup"><span data-stu-id="2099f-106">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://devblogs.microsoft.com/dotnet/feed/).</span></span>  
  
2. <span data-ttu-id="2099f-107">A página com o botão direito e selecione **Exibir código-fonte**.</span><span class="sxs-lookup"><span data-stu-id="2099f-107">Right-click the page and select **View Source**.</span></span>  
  
3. <span data-ttu-id="2099f-108">Copie o texto do feed pressionando **Ctrl + T** para selecionar todo o texto, e **Ctrl + C** para copiar.</span><span class="sxs-lookup"><span data-stu-id="2099f-108">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="2099f-109">Criar os tipos de dados</span><span class="sxs-lookup"><span data-stu-id="2099f-109">Creating the data types</span></span>  
  
1. <span data-ttu-id="2099f-110">Abra um arquivo de código em que o proxy deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="2099f-110">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="2099f-111">Esse arquivo deve ser parte de um projeto do .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="2099f-111">This file should be part of a .NET Framework 4.5 project.</span></span>  
  
2. <span data-ttu-id="2099f-112">Coloque o cursor em um local no arquivo fora de qualquer classe existente.</span><span class="sxs-lookup"><span data-stu-id="2099f-112">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3. <span data-ttu-id="2099f-113">Selecione **edite**, **Colar especial**, **colar XML como Classes**.</span><span class="sxs-lookup"><span data-stu-id="2099f-113">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4. <span data-ttu-id="2099f-114">Classes chamadas `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` e `rssChannelItemGuid` são criados com os membros necessários para acessar os elementos no RSS feed.</span><span class="sxs-lookup"><span data-stu-id="2099f-114">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="2099f-115">Usando as classes geradas</span><span class="sxs-lookup"><span data-stu-id="2099f-115">Using the generated classes</span></span>  
  
1. <span data-ttu-id="2099f-116">Depois que as classes são geradas, pode ser usados no código como quaisquer outras classes.</span><span class="sxs-lookup"><span data-stu-id="2099f-116">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="2099f-117">O exemplo de código a seguir retorna uma nova instância do `rssChannelImage` classe.</span><span class="sxs-lookup"><span data-stu-id="2099f-117">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
