---
title: Suporte do namespace em DOM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0548ead-0fed-41ee-b33e-117ba900d3bc
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3145df6517df9db580bfcc5d67edd9d1a61f290b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="namespace-support-in-the-dom"></a><span data-ttu-id="e05dd-102">Suporte do namespace em DOM</span><span class="sxs-lookup"><span data-stu-id="e05dd-102">Namespace Support in the DOM</span></span>
<span data-ttu-id="e05dd-103">O modelo de objeto (DOM) de documento XML é completamente URL ciente.</span><span class="sxs-lookup"><span data-stu-id="e05dd-103">The XML Document Object Model (DOM) is completely namespace-aware.</span></span> <span data-ttu-id="e05dd-104">Somente os documentos XML URL cientes são suportados.</span><span class="sxs-lookup"><span data-stu-id="e05dd-104">Only namespace-aware XML documents are supported.</span></span> <span data-ttu-id="e05dd-105">World Wide Web Consortium (W3C) especifica que os aplicativos DOM que o nível de implementar 1 pode estar ciente não-namespace-, e os recursos do nível 2 DOM são cientes URL.</span><span class="sxs-lookup"><span data-stu-id="e05dd-105">The World Wide Web Consortium (W3C) specifies that DOM applications that implement Level 1 can be non-namespace-aware, and DOM Level 2 features are namespace-aware.</span></span> <span data-ttu-id="e05dd-106">No entanto, todos os recursos em DOM XML são cientes URL, indiferente se o método é recomendação DOM nível de nível 1 ou 2.</span><span class="sxs-lookup"><span data-stu-id="e05dd-106">However, all features in the XML DOM are namespace-aware, regardless if the method is from the Level 1 or Level 2 DOM Recommendation.</span></span>  
  
 <span data-ttu-id="e05dd-107">Por exemplo, em uma configuração não-namespace- ciente, a chamada `setAttribute("A:b", "123")`, conforme especificado na recomendação de nível 1 DOM, não resulta em um atributo com um prefixo de `A` e um nome local de `b`.</span><span class="sxs-lookup"><span data-stu-id="e05dd-107">For example, in a non-namespace-aware setting, calling `setAttribute("A:b", "123")`, as specified in the DOM Level 1 Recommendation, does not result in an attribute with a prefix of `A` and a local name of `b`.</span></span> <span data-ttu-id="e05dd-108">Resultaria em um atributo com o valor `A:b`.</span><span class="sxs-lookup"><span data-stu-id="e05dd-108">It would result in an attribute with the value `A:b`.</span></span>  
  
 <span data-ttu-id="e05dd-109">Em um ambiente URL ciente, na chamada a resultados de `setAttribute("A:b", "123")` de nível 2 DOM em um atributo com um prefixo de `A` e um nome local de `b`.</span><span class="sxs-lookup"><span data-stu-id="e05dd-109">In a namespace-aware environment, the call to the DOM Level 2 `setAttribute("A:b", "123")` results in an attribute with a prefix of `A` and a local name of `b`.</span></span> <span data-ttu-id="e05dd-110">Isso é como funciona o DOM do Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e05dd-110">This is how the Microsoft .NET Framework DOM works.</span></span>  
  
 <span data-ttu-id="e05dd-111">Portanto, para todos os métodos que têm um parâmetro de nome, esses métodos também têm um prefixo para qualificar o nome.</span><span class="sxs-lookup"><span data-stu-id="e05dd-111">Therefore, for all methods that take a name parameter, these methods also take a prefix to qualify the name.</span></span> <span data-ttu-id="e05dd-112">O parâmetro de nome, como o `A:b` no **setAttribute** método DOM nível 1, é analisado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e05dd-112">The name parameter, such as the `A:b` in the **setAttribute** DOM Level 1 method, is parsed as follows:</span></span>  
  
-   <span data-ttu-id="e05dd-113">Se não houver nenhum caractere dois-pontos (:), então o nome local é definido para o parâmetro de `name` , e o prefixo e o NamespaceURI são cadeias de caracteres vazias.</span><span class="sxs-lookup"><span data-stu-id="e05dd-113">If there are no colon (:) characters, then the local name is set to the `name` parameter, and the prefix and NamespaceURI are empty strings.</span></span>  
  
-   <span data-ttu-id="e05dd-114">Se um dois-pontos é encontrado, o nome é dividido em duas partes com base na posição do primeiro caractere dois-pontos.</span><span class="sxs-lookup"><span data-stu-id="e05dd-114">If a colon is found, then the name is split into two parts based on the position of the first colon character.</span></span> <span data-ttu-id="e05dd-115">O prefixo é definido para a cadeia de caracteres encontrada antes de pontos, e o nome local é definido para a cadeia de caracteres encontrada após os dois-pontos.</span><span class="sxs-lookup"><span data-stu-id="e05dd-115">The prefix is set to the string found before the colon, and local name is set to the string found after the colon.</span></span> <span data-ttu-id="e05dd-116">Para os métodos que não têm um valor de NamespaceURI, o NamespaceURI não é resolvido e o não são definidas para a cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="e05dd-116">For methods that do not take a NamespaceURI value, the NamespaceURI is not resolved and remains set to empty string.</span></span> <span data-ttu-id="e05dd-117">Caso contrário, o NamespaceURI é definido para a cadeia de caracteres passada para o método.</span><span class="sxs-lookup"><span data-stu-id="e05dd-117">Otherwise, the NamespaceURI is set to the string passed to the method.</span></span> <span data-ttu-id="e05dd-118">Se o prefixo for indefinido, o **salvar** método e **InnerXml** e **OuterXml** propriedades falhar.</span><span class="sxs-lookup"><span data-stu-id="e05dd-118">If the prefix is undefined, then the **Save** method and **InnerXml** and **OuterXml** properties fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e05dd-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e05dd-119">See Also</span></span>  
 [<span data-ttu-id="e05dd-120">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="e05dd-120">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
