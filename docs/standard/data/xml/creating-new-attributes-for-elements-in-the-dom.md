---
title: Criando novos atributos para elementos no DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 870e800220031338557792fa612d4a3101e79f90
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48024565"
---
# <a name="creating-new-attributes-for-elements-in-the-dom"></a><span data-ttu-id="cbb4e-102">Criando novos atributos para elementos no DOM</span><span class="sxs-lookup"><span data-stu-id="cbb4e-102">Creating New Attributes for Elements in the DOM</span></span>
<span data-ttu-id="cbb4e-103">Criar novos atributos é diferente de criar outros tipos de nó, pois os atributos não são nós, mas propriedades de um nó de elemento e estão contidos em um **XmlAttributeCollection** associado ao elemento.</span><span class="sxs-lookup"><span data-stu-id="cbb4e-103">Creating new attributes is different than creating other node types, because attributes are not nodes, but are properties of an element node and are contained in an **XmlAttributeCollection** associated with the element.</span></span> <span data-ttu-id="cbb4e-104">Há várias maneiras de criar um atributo e anexá-lo a um elemento:</span><span class="sxs-lookup"><span data-stu-id="cbb4e-104">There are multiple ways to create an attribute and attach it to an element:</span></span>  
  
-   <span data-ttu-id="cbb4e-105">Obter o nó de elemento e usar **SetAttribute** para adicionar um atributo à coleção de atributos do elemento.</span><span class="sxs-lookup"><span data-stu-id="cbb4e-105">Get the element node and use **SetAttribute** to add an attribute to the attribute collection of that element.</span></span>  
  
-   <span data-ttu-id="cbb4e-106">Criar um nó **XmlAttribute** usando o método **CreateAttribute**, obter o nó do elemento e usar **SetAttributeNode** para adicionar o nó à coleção de atributos desse elemento.</span><span class="sxs-lookup"><span data-stu-id="cbb4e-106">Create an **XmlAttribute** node using the **CreateAttribute** method, get the element node, then use **SetAttributeNode** to add the node to the attribute collection of that element.</span></span>  
  
 <span data-ttu-id="cbb4e-107">O exemplo a seguir mostra como adicionar um atributo a um elemento usando o método **SetAttribute**.</span><span class="sxs-lookup"><span data-stu-id="cbb4e-107">The following example shows how to add an attribute to an element using the **SetAttribute** method.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
public class Sample  
  
  public shared sub Main()  
  
  Dim doc as XmlDocument = new XmlDocument()  
  doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" & _  
              "<title>Pride And Prejudice</title>" & _  
              "</book>")  
  Dim root as XmlElement = doc.DocumentElement  
  
  'Add a new attribute.  
  root.SetAttribute("genre", "urn:samples", "novel")  
  
  Console.WriteLine("Display the modified XML...")  
  Console.WriteLine(doc.InnerXml)  
  
  end sub  
end class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  public static void Main()  
  {  
    XmlDocument doc = new XmlDocument();  
    doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" +  
                "<title>Pride And Prejudice</title>" +  
                "</book>");  
    XmlElement root = doc.DocumentElement;  
  
    // Add a new attribute.  
    root.SetAttribute("genre", "urn:samples", "novel");  
  
    Console.WriteLine("Display the modified XML...");  
    Console.WriteLine(doc.InnerXml);  
  }  
```  
  
 <span data-ttu-id="cbb4e-108">O exemplo a seguir mostra um novo atributo criado usando o método **CreateAttribute**.</span><span class="sxs-lookup"><span data-stu-id="cbb4e-108">The following example shows a new attribute being created using the **CreateAttribute** method.</span></span> <span data-ttu-id="cbb4e-109">Em seguida, ele mostra o atributo adicionado à coleção de atributos do elemento **book** usando o método **SetAttributeNode**.</span><span class="sxs-lookup"><span data-stu-id="cbb4e-109">It then shows the attribute added to the attribute collection of the **book** element using the **SetAttributeNode** method.</span></span>  
  
 <span data-ttu-id="cbb4e-110">Com o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="cbb4e-110">Given the following XML:</span></span>  
  
```xml  
<book genre='novel' ISBN='1-861001-57-5'>  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 <span data-ttu-id="cbb4e-111">crie um novo atributo e atribua um valor a ele:</span><span class="sxs-lookup"><span data-stu-id="cbb4e-111">create a new attribute and give it a value:</span></span>  
  
```vb  
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")  
   attr.Value = "WorldWide Publishing"  
```  
  
```csharp  
XmlAttribute attr = doc.CreateAttribute("publisher");  
attr.Value = "WorldWide Publishing";  
```  
  
 <span data-ttu-id="cbb4e-112">e anexe-o ao elemento:</span><span class="sxs-lookup"><span data-stu-id="cbb4e-112">and attach it to the element:</span></span>  
  
```vb  
doc.DocumentElement.SetAttributeNode(attr)  
```  
  
```csharp  
doc.DocumentElement.SetAttributeNode(attr);  
```  
  
 <span data-ttu-id="cbb4e-113">**Saída**</span><span class="sxs-lookup"><span data-stu-id="cbb4e-113">**Output**</span></span>  
  
```xml  
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 <span data-ttu-id="cbb4e-114">O exemplo de código completo pode ser encontrado em <xref:System.Xml.XmlDocument.CreateAttribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="cbb4e-114">The full code sample can be found at <xref:System.Xml.XmlDocument.CreateAttribute%2A>.</span></span>  
  
 <span data-ttu-id="cbb4e-115">Você também pode criar um nó **XmlAttribute** e usar o método **InsertBefore** ou **InsertAfter** para colocá-lo na posição apropriada na coleção.</span><span class="sxs-lookup"><span data-stu-id="cbb4e-115">You can also create an **XmlAttribute** node and use the **InsertBefore** or **InsertAfter** methods to place it in the appropriate position in the collection.</span></span> <span data-ttu-id="cbb4e-116">Se um atributo com o mesmo nome já estiver presente na coleção de atributos, o nó **XmlAttribute** existente será removido da coleção, e o novo nó **XmlAttribute** será inserido.</span><span class="sxs-lookup"><span data-stu-id="cbb4e-116">If an attribute with the same name is already present in the attribute collection, the existing **XmlAttribute** node is removed from the collection and the new **XmlAttribute** node is inserted.</span></span> <span data-ttu-id="cbb4e-117">Isso é executado da mesma forma que o método **SetAttribute**.</span><span class="sxs-lookup"><span data-stu-id="cbb4e-117">This performs the same way as the **SetAttribute** method.</span></span> <span data-ttu-id="cbb4e-118">Esses métodos usam, como parâmetro, um nó existente como um ponto de referência para fazer **InsertBefore** e **InsertAfter**.</span><span class="sxs-lookup"><span data-stu-id="cbb4e-118">These methods take, as a parameter, an existing node as a reference point to do the **InsertBefore** and **InsertAfter**.</span></span> <span data-ttu-id="cbb4e-119">Se você não fornecer um nó de referência indicando onde inserir o novo nó, o padrão para o método **InsertAfter** será inserir o novo nó no início da coleção.</span><span class="sxs-lookup"><span data-stu-id="cbb4e-119">If you do not provide a reference node indicating where to insert the new node, the default for the **InsertAfter** method is to insert the new node at the beginning of the collection.</span></span> <span data-ttu-id="cbb4e-120">A posição padrão de **InsertBefore**, se nenhum nó de referência for fornecido, será no final da coleção.</span><span class="sxs-lookup"><span data-stu-id="cbb4e-120">The default position for the **InsertBefore**, if no reference node is provided, is at the end of the collection.</span></span>  
  
 <span data-ttu-id="cbb4e-121">Se você criou um **XmlNamedNodeMap** de atributos, poderá adicionar um atributo pelo nome usando <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="cbb4e-121">If you created an **XmlNamedNodeMap** of attributes, you can add an attribute by name using the <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>.</span></span> <span data-ttu-id="cbb4e-122">Para saber mais, confira [Coleções de nó em NamedNodeMaps e em NodeLists](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md).</span><span class="sxs-lookup"><span data-stu-id="cbb4e-122">For more information, see [Node Collections in NamedNodeMaps and NodeLists](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md).</span></span>  
  
## <a name="default-attributes"></a><span data-ttu-id="cbb4e-123">Atributos padrão</span><span class="sxs-lookup"><span data-stu-id="cbb4e-123">Default Attributes</span></span>  
 <span data-ttu-id="cbb4e-124">Se você criar um elemento que está declarado para ter um atributo padrão, um novo atributo padrão com seu valor padrão será criado pelo DOM (Document Object Model) XML e anexado ao elemento.</span><span class="sxs-lookup"><span data-stu-id="cbb4e-124">If you create an element that is declared to have a default attribute, then a new default attribute with its default value is created by the XML Document Object Model (DOM) and attached to the element.</span></span> <span data-ttu-id="cbb4e-125">Os nós filhos do atributo padrão também são criados neste momento.</span><span class="sxs-lookup"><span data-stu-id="cbb4e-125">The child nodes of the default attribute are also created at this time.</span></span>  
  
## <a name="attribute-child-nodes"></a><span data-ttu-id="cbb4e-126">Nós filhos do atributo</span><span class="sxs-lookup"><span data-stu-id="cbb4e-126">Attribute Child Nodes</span></span>  
 <span data-ttu-id="cbb4e-127">O valor de um nó de atributo se torna os seus nós filhos.</span><span class="sxs-lookup"><span data-stu-id="cbb4e-127">The value of an attribute node becomes its child nodes.</span></span> <span data-ttu-id="cbb4e-128">Há apenas dois tipos de nós filhos válidos: nós **XmlText** e nós **XmlEntityReference**.</span><span class="sxs-lookup"><span data-stu-id="cbb4e-128">There are only two types of valid child nodes: **XmlText** nodes, and **XmlEntityReference** nodes.</span></span> <span data-ttu-id="cbb4e-129">Esses são nós filhos no sentido de que métodos como **FirstChild** e **LastChild** os processam como nós filhos.</span><span class="sxs-lookup"><span data-stu-id="cbb4e-129">These are child nodes in the sense that methods such as **FirstChild** and **LastChild** process them as child nodes.</span></span> <span data-ttu-id="cbb4e-130">Essa distinção de um atributo que possui nós filhos é importante ao tentar remover atributos ou nós filhos do atributo.</span><span class="sxs-lookup"><span data-stu-id="cbb4e-130">This distinction of an attribute having child nodes is important when trying to remove attributes or attribute child nodes.</span></span> <span data-ttu-id="cbb4e-131">Para saber mais, confira [Removendo atributos de um nó de elemento no DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="cbb4e-131">For more information, see [Removing Attributes from an Element Node in the DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbb4e-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cbb4e-132">See also</span></span>

- [<span data-ttu-id="cbb4e-133">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="cbb4e-133">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
