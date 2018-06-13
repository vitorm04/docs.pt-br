---
title: Alterando propriedades de prefixo de namespace
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e3f41ba7281d67cc2ce848597926f5efebf4d489
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568687"
---
# <a name="changing-namespace-prefix-properties"></a><span data-ttu-id="b7005-102">Alterando propriedades de prefixo de namespace</span><span class="sxs-lookup"><span data-stu-id="b7005-102">Changing Namespace Prefix Properties</span></span>
<span data-ttu-id="b7005-103">A classe **XmlNode** permite que você modifique o prefixo de namespace associado a um nó específico.</span><span class="sxs-lookup"><span data-stu-id="b7005-103">The **XmlNode** class allows you to change the namespace prefix associated with a given node.</span></span> <span data-ttu-id="b7005-104">Por exemplo, o código a seguir mostra o prefixo de um elemento que está sendo alterado.</span><span class="sxs-lookup"><span data-stu-id="b7005-104">For example, the following code shows the prefix of an element being changed.</span></span>  
  
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
  
 <span data-ttu-id="b7005-105">**Saída**</span><span class="sxs-lookup"><span data-stu-id="b7005-105">**Output**</span></span>  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 <span data-ttu-id="b7005-106">Altere o prefixo de um nó não altera seu namespace.</span><span class="sxs-lookup"><span data-stu-id="b7005-106">Changing the prefix of a node does not change its namespace.</span></span> <span data-ttu-id="b7005-107">O namespace somente pode ser definida quando o nó é criado.</span><span class="sxs-lookup"><span data-stu-id="b7005-107">The namespace can only be set when the node is created.</span></span> <span data-ttu-id="b7005-108">Quando você mantém a árvore, novos atributos de namespace podem ser persistentes para fora para satisfazer o prefixo você definir.</span><span class="sxs-lookup"><span data-stu-id="b7005-108">When you persist the tree, new namespace attributes may be persisted out to satisfy the prefix you set.</span></span> <span data-ttu-id="b7005-109">Se o novo namespace não pode ser criada, então o prefixo é alterado para que as conservas do nó seu nome e local namespace.</span><span class="sxs-lookup"><span data-stu-id="b7005-109">If the new namespace cannot be created, then the prefix is changed so the node preserves its local name and namespace.</span></span> <span data-ttu-id="b7005-110">O exemplo a seguir mostra um atributo do namespace sendo adicionado.</span><span class="sxs-lookup"><span data-stu-id="b7005-110">The following example shows a namespace attribute being added.</span></span>  
  
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
  
 <span data-ttu-id="b7005-111">**Saída**</span><span class="sxs-lookup"><span data-stu-id="b7005-111">**Output**</span></span>  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 <span data-ttu-id="b7005-112">Quando a árvore foi mantida em uma cadeia de caracteres como resultado da chamada a **doc.InnerXml**, o atributo `xmlns:a='123'` foi adicionado para preservar o namespace do elemento `test`.</span><span class="sxs-lookup"><span data-stu-id="b7005-112">When the tree was persisted to a string as a result of the call to **doc.InnerXml**, the `xmlns:a='123'` attribute was added to preserve the namespace of the `test` element.</span></span> <span data-ttu-id="b7005-113">Foi `'123'`, e permanece `'123'`.</span><span class="sxs-lookup"><span data-stu-id="b7005-113">It was `'123'`, and it remained `'123'`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7005-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7005-114">See Also</span></span>  
 [<span data-ttu-id="b7005-115">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="b7005-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
