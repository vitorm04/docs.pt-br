---
title: Alterando propriedades de prefixo de namespace
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
ms.openlocfilehash: b817a68ff9789be414118ff4c1a3d88ca3ea9f01
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290909"
---
# <a name="changing-namespace-prefix-properties"></a><span data-ttu-id="5c597-102">Alterando propriedades de prefixo de namespace</span><span class="sxs-lookup"><span data-stu-id="5c597-102">Changing Namespace Prefix Properties</span></span>
<span data-ttu-id="5c597-103">A classe **XmlNode** permite que você modifique o prefixo de namespace associado a um nó específico.</span><span class="sxs-lookup"><span data-stu-id="5c597-103">The **XmlNode** class allows you to change the namespace prefix associated with a given node.</span></span> <span data-ttu-id="5c597-104">Por exemplo, o código a seguir mostra o prefixo de um elemento que está sendo alterado.</span><span class="sxs-lookup"><span data-stu-id="5c597-104">For example, the following code shows the prefix of an element being changed.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "b"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>");  
XmlElement e = doc.DocumentElement;
e.Prefix = "b";  
Console.WriteLine(doc.InnerXml);  
```  
  
 <span data-ttu-id="5c597-105">**Saída**</span><span class="sxs-lookup"><span data-stu-id="5c597-105">**Output**</span></span>  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 <span data-ttu-id="5c597-106">Altere o prefixo de um nó não altera seu namespace.</span><span class="sxs-lookup"><span data-stu-id="5c597-106">Changing the prefix of a node does not change its namespace.</span></span> <span data-ttu-id="5c597-107">O namespace somente pode ser definida quando o nó é criado.</span><span class="sxs-lookup"><span data-stu-id="5c597-107">The namespace can only be set when the node is created.</span></span> <span data-ttu-id="5c597-108">Quando você mantém a árvore, novos atributos de namespace podem ser persistentes para fora para satisfazer o prefixo você definir.</span><span class="sxs-lookup"><span data-stu-id="5c597-108">When you persist the tree, new namespace attributes may be persisted out to satisfy the prefix you set.</span></span> <span data-ttu-id="5c597-109">Se o novo namespace não pode ser criada, então o prefixo é alterado para que as conservas do nó seu nome e local namespace.</span><span class="sxs-lookup"><span data-stu-id="5c597-109">If the new namespace cannot be created, then the prefix is changed so the node preserves its local name and namespace.</span></span> <span data-ttu-id="5c597-110">O exemplo a seguir mostra um atributo do namespace sendo adicionado.</span><span class="sxs-lookup"><span data-stu-id="5c597-110">The following example shows a namespace attribute being added.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<test xmlns='123'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "a"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<test xmlns='123'/>");  
XmlElement e = doc.DocumentElement;
e.Prefix = "a";  
Console.WriteLine(doc.InnerXml);  
```  
  
 <span data-ttu-id="5c597-111">**Saída**</span><span class="sxs-lookup"><span data-stu-id="5c597-111">**Output**</span></span>  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 <span data-ttu-id="5c597-112">Quando a árvore foi mantida em uma cadeia de caracteres como resultado da chamada a **doc.InnerXml**, o atributo `xmlns:a='123'` foi adicionado para preservar o namespace do elemento `test`.</span><span class="sxs-lookup"><span data-stu-id="5c597-112">When the tree was persisted to a string as a result of the call to **doc.InnerXml**, the `xmlns:a='123'` attribute was added to preserve the namespace of the `test` element.</span></span> <span data-ttu-id="5c597-113">Foi `'123'`, e permanece `'123'`.</span><span class="sxs-lookup"><span data-stu-id="5c597-113">It was `'123'`, and it remained `'123'`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c597-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="5c597-114">See also</span></span>

- [<span data-ttu-id="5c597-115">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="5c597-115">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
