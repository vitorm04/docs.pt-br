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
ms.openlocfilehash: 4d6e738f4e3a47d73e37c395dd74fe19e99d81bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353187"
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="5e58a-102">Operador GetXmlNamespace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e58a-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="5e58a-103">Obtém o objeto de <xref:System.Xml.Linq.XNamespace> que corresponde ao prefixo de namespace XML especificado.</span><span class="sxs-lookup"><span data-stu-id="5e58a-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e58a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e58a-104">Syntax</span></span>  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="5e58a-105">Partes</span><span class="sxs-lookup"><span data-stu-id="5e58a-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="5e58a-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5e58a-106">Optional.</span></span> <span data-ttu-id="5e58a-107">A cadeia de caracteres que identifica o prefixo do namespace XML.</span><span class="sxs-lookup"><span data-stu-id="5e58a-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="5e58a-108">Se fornecido, essa cadeia de caracteres deve ser um identificador XML válido.</span><span class="sxs-lookup"><span data-stu-id="5e58a-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="5e58a-109">Para obter mais informações, consulte [nomes de elementos XML declarados e atributos](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5e58a-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="5e58a-110">Se nenhum prefixo for especificado, o namespace padrão será retornado.</span><span class="sxs-lookup"><span data-stu-id="5e58a-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="5e58a-111">Se nenhum namespace padrão for especificado, o namespace vazio será retornado.</span><span class="sxs-lookup"><span data-stu-id="5e58a-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e58a-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="5e58a-112">Return Value</span></span>  
 <span data-ttu-id="5e58a-113">O objeto <xref:System.Xml.Linq.XNamespace> que corresponde ao prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="5e58a-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e58a-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="5e58a-114">Remarks</span></span>  
 <span data-ttu-id="5e58a-115">O operador `GetXmlNamespace` Obtém o objeto <xref:System.Xml.Linq.XNamespace> que corresponde ao prefixo do namespace XML `xmlNamespacePrefix`.</span><span class="sxs-lookup"><span data-stu-id="5e58a-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="5e58a-116">Você pode usar prefixos de namespace XML diretamente em literais XML e propriedades de eixo XML.</span><span class="sxs-lookup"><span data-stu-id="5e58a-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="5e58a-117">No entanto, você deve usar o operador `GetXmlNamespace` para converter um prefixo de namespace em um objeto <xref:System.Xml.Linq.XNamespace> antes de poder usá-lo em seu código.</span><span class="sxs-lookup"><span data-stu-id="5e58a-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="5e58a-118">Você pode acrescentar um nome de elemento não qualificado a um objeto <xref:System.Xml.Linq.XNamespace> para obter um objeto <xref:System.Xml.Linq.XName> totalmente qualificado, que muitos métodos [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] exigem.</span><span class="sxs-lookup"><span data-stu-id="5e58a-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e58a-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5e58a-119">Example</span></span>  
 <span data-ttu-id="5e58a-120">O exemplo a seguir importa `ns` como um prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="5e58a-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="5e58a-121">Em seguida, ele usa o prefixo do namespace para criar um literal XML e acessar o primeiro nó filho que tem o nome qualificado `ns:phone`.</span><span class="sxs-lookup"><span data-stu-id="5e58a-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="5e58a-122">Em seguida, ele passa esse nó filho para a sub-rotina `ShowName`, que constrói um nome qualificado usando o operador `GetXmlNamespace`.</span><span class="sxs-lookup"><span data-stu-id="5e58a-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="5e58a-123">Em seguida, a sub-rotina `ShowName` passa o nome qualificado para o método <xref:System.Xml.Linq.XNode.Ancestors%2A> para obter o nó pai `ns:contact`.</span><span class="sxs-lookup"><span data-stu-id="5e58a-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 <span data-ttu-id="5e58a-124">Quando você chama `TestGetXmlNamespace.RunSample()`, ele exibe uma caixa de mensagem que contém o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="5e58a-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="5e58a-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e58a-125">See also</span></span>

- [<span data-ttu-id="5e58a-126">Instrução Imports (Namespace de XML)</span><span class="sxs-lookup"><span data-stu-id="5e58a-126">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="5e58a-127">Acessando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e58a-127">Accessing XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
