---
title: Namespaces e DTDs em DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc8a1de8ab10eff88757720a35aa9668125cfbfa
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582155"
---
# <a name="namespaces-and-dtds-in-the-dom"></a><span data-ttu-id="b1a45-102">Namespaces e DTDs em DOM</span><span class="sxs-lookup"><span data-stu-id="b1a45-102">Namespaces and DTDs in the DOM</span></span>
<span data-ttu-id="b1a45-103">Definições de tipo (DTDs) de documento complicam suporte de namespace.</span><span class="sxs-lookup"><span data-stu-id="b1a45-103">Document type definitions (DTDs) complicate namespace support.</span></span> <span data-ttu-id="b1a45-104">Por exemplo, o seguinte XML contém os atributos padrões que contém dois-pontos em seus nomes.</span><span class="sxs-lookup"><span data-stu-id="b1a45-104">For example, the following XML contains default attributes containing colons in their names.</span></span>  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 <span data-ttu-id="b1a45-105">Os seguintes são possíveis resoluções se esta compilação é permitida:</span><span class="sxs-lookup"><span data-stu-id="b1a45-105">The following are possible resolutions if this construct is allowed:</span></span>  
  
-   <span data-ttu-id="b1a45-106">`x:` é tratado como um prefixo de namespace, mas esse prefixo deve ser resolvível usando uma declaração de namespace de `xmlns:x` , que também deve existir em qualquer lugar no DTD.</span><span class="sxs-lookup"><span data-stu-id="b1a45-106">The `x:` is treated as a namespace prefix, but this prefix must be resolvable using an `xmlns:x` namespace declaration, which must also exist somewhere in the DTD.</span></span> <span data-ttu-id="b1a45-107">É um erro para mapear esse prefixo a algo diferente no documento de instância.</span><span class="sxs-lookup"><span data-stu-id="b1a45-107">It is an error to map this prefix to something different in the instance document.</span></span>  
  
-   <span data-ttu-id="b1a45-108">`x:` é tratado como um prefixo de namespace, mas esse prefixo é sempre resolvido no contexto de elementos da instância.</span><span class="sxs-lookup"><span data-stu-id="b1a45-108">The `x:` is treated as a namespace prefix, but this prefix is always resolved in the context of the instance elements.</span></span> <span data-ttu-id="b1a45-109">Isso significa que o prefixo pode realmente mapear ao namespace diferente de recurso uniformes (URIs), dependendo do escopo de namespace no qual o elemento de `item` aparece.</span><span class="sxs-lookup"><span data-stu-id="b1a45-109">This means the prefix could actually map to different namespace Uniform Resource Identifiers (URIs), depending on the namespace scope in which the `item` element appears.</span></span> <span data-ttu-id="b1a45-110">Esse comportamento é mais previsível da resolução determinada no marcador anterior, mas tem outras ramificação complicadas porque ela requer os atributos padrão é materializado.</span><span class="sxs-lookup"><span data-stu-id="b1a45-110">This behavior is more predictable than the resolution given in the earlier bullet, but it has other complicated ramifications because it requires the default attributes be materialized.</span></span>  
  
-   <span data-ttu-id="b1a45-111">O separador dois-pontos é ignorada porque ele é um DTD, e o nome do atributo é `x:y`, nenhum prefixo e nenhum URI de namespace.</span><span class="sxs-lookup"><span data-stu-id="b1a45-111">The colon is ignored because it is in a DTD, and the name of the attribute is `x:y`, no prefix and no namespace URI.</span></span>  
  
-   <span data-ttu-id="b1a45-112">O separador dois-pontos no atributo padrão gerencie uma exceção, dizer que os dois-pontos nos nomes em um DTD não são suportados.</span><span class="sxs-lookup"><span data-stu-id="b1a45-112">The colon in the default attribute throws an exception, saying that colons in names inside a DTD are not supported.</span></span> <span data-ttu-id="b1a45-113">Isso resulta em um comportamento previsível, mas mídia que você não pode carregar muitos do World Wide Web Consortium DTDs publicado (W3C).</span><span class="sxs-lookup"><span data-stu-id="b1a45-113">This results in a predictable behavior, but means you cannot load many of the World Wide Web Consortium (W3C) published DTDs.</span></span>  
  
-   <span data-ttu-id="b1a45-114">Quando a validação de DTD de um usuário, suporte de namespace para o documento inteiro é desativada.</span><span class="sxs-lookup"><span data-stu-id="b1a45-114">When the user requests DTD validation, namespace support for the entire document is turned off.</span></span> <span data-ttu-id="b1a45-115">Isso torna possível carregar o W3C DTDs e resultados em um comportamento previsível.</span><span class="sxs-lookup"><span data-stu-id="b1a45-115">This makes it possible to load W3C DTDs and results in a predictable behavior.</span></span>  
  
 <span data-ttu-id="b1a45-116">O XML no Microsoft .NET Framework implementa a segunda opção para compatibilidade máxima com o W3C.</span><span class="sxs-lookup"><span data-stu-id="b1a45-116">The XML in the Microsoft .NET Framework implements the second option for maximum W3C compatibility.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1a45-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1a45-117">See also</span></span>

- [<span data-ttu-id="b1a45-118">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="b1a45-118">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
