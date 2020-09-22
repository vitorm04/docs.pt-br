---
title: Operador GetXmlNamespace
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: 660474c1193076755889fd885c1b78bec78f0a2c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873466"
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="b66fb-102">Operador GetXmlNamespace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b66fb-102">GetXmlNamespace Operator (Visual Basic)</span></span>

<span data-ttu-id="b66fb-103">Obtém o <xref:System.Xml.Linq.XNamespace> objeto que corresponde ao prefixo de namespace XML especificado.</span><span class="sxs-lookup"><span data-stu-id="b66fb-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b66fb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b66fb-104">Syntax</span></span>  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="b66fb-105">Partes</span><span class="sxs-lookup"><span data-stu-id="b66fb-105">Parts</span></span>  

 `xmlNamespacePrefix`  
 <span data-ttu-id="b66fb-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b66fb-106">Optional.</span></span> <span data-ttu-id="b66fb-107">A cadeia de caracteres que identifica o prefixo do namespace XML.</span><span class="sxs-lookup"><span data-stu-id="b66fb-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="b66fb-108">Se fornecido, essa cadeia de caracteres deve ser um identificador XML válido.</span><span class="sxs-lookup"><span data-stu-id="b66fb-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="b66fb-109">Para obter mais informações, consulte [nomes de elementos XML declarados e atributos](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b66fb-109">For more information, see [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="b66fb-110">Se nenhum prefixo for especificado, o namespace padrão será retornado.</span><span class="sxs-lookup"><span data-stu-id="b66fb-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="b66fb-111">Se nenhum namespace padrão for especificado, o namespace vazio será retornado.</span><span class="sxs-lookup"><span data-stu-id="b66fb-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b66fb-112">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="b66fb-112">Return Value</span></span>  

 <span data-ttu-id="b66fb-113">O <xref:System.Xml.Linq.XNamespace> objeto que corresponde ao prefixo do namespace XML.</span><span class="sxs-lookup"><span data-stu-id="b66fb-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b66fb-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="b66fb-114">Remarks</span></span>  

 <span data-ttu-id="b66fb-115">O `GetXmlNamespace` operador Obtém o <xref:System.Xml.Linq.XNamespace> objeto que corresponde ao prefixo de namespace XML `xmlNamespacePrefix` .</span><span class="sxs-lookup"><span data-stu-id="b66fb-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="b66fb-116">Você pode usar prefixos de namespace XML diretamente em literais XML e propriedades de eixo XML.</span><span class="sxs-lookup"><span data-stu-id="b66fb-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="b66fb-117">No entanto, você deve usar o `GetXmlNamespace` operador para converter um prefixo de namespace em um <xref:System.Xml.Linq.XNamespace> objeto antes de poder usá-lo em seu código.</span><span class="sxs-lookup"><span data-stu-id="b66fb-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="b66fb-118">Você pode acrescentar um nome de elemento não qualificado a um <xref:System.Xml.Linq.XNamespace> objeto para obter um objeto totalmente qualificado <xref:System.Xml.Linq.XName> , que muitos [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] métodos exigem.</span><span class="sxs-lookup"><span data-stu-id="b66fb-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b66fb-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b66fb-119">Example</span></span>  

 <span data-ttu-id="b66fb-120">O exemplo a seguir importa `ns` como um prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="b66fb-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="b66fb-121">Em seguida, ele usa o prefixo do namespace para criar um literal XML e acessar o primeiro nó filho que tem o nome qualificado `ns:phone` .</span><span class="sxs-lookup"><span data-stu-id="b66fb-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="b66fb-122">Em seguida, ele passa esse nó filho para a `ShowName` sub-rotina, que constrói um nome qualificado usando o `GetXmlNamespace` operador.</span><span class="sxs-lookup"><span data-stu-id="b66fb-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="b66fb-123">`ShowName`Em seguida, a sub-rotina passa o nome qualificado para o <xref:System.Xml.Linq.XNode.Ancestors%2A> método para obter o `ns:contact` nó pai.</span><span class="sxs-lookup"><span data-stu-id="b66fb-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 <span data-ttu-id="b66fb-124">Quando você chama `TestGetXmlNamespace.RunSample()` , ele exibe uma caixa de mensagem que contém o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="b66fb-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="b66fb-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="b66fb-125">See also</span></span>

- [<span data-ttu-id="b66fb-126">Instrução Imports (namespace XML)</span><span class="sxs-lookup"><span data-stu-id="b66fb-126">Imports Statement (XML Namespace)</span></span>](../statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="b66fb-127">Acessando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b66fb-127">Accessing XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/accessing-xml.md)
