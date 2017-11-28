---
title: "Funções definidas pelo usuário e variáveis"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 4772f20e-1e7f-496e-93c2-1484473be555
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e1327ac2a3df7a84c157e4bf60d2ad63d69b1677
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="user-defined-functions-and-variables"></a><span data-ttu-id="915fb-102">Funções definidas pelo usuário e variáveis</span><span class="sxs-lookup"><span data-stu-id="915fb-102">User Defined Functions and Variables</span></span>
<span data-ttu-id="915fb-103">A classe de <xref:System.Xml.XPath.XPathNavigator> fornece um conjunto de métodos que são usados para interagir com os dados de <xref:System.Xml.XPath.XPathDocument> .</span><span class="sxs-lookup"><span data-stu-id="915fb-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods that are used to interact with <xref:System.Xml.XPath.XPathDocument> data.</span></span> <span data-ttu-id="915fb-104">Você pode complementar as funções padrão XPath implementando funções e variáveis de extensão para o uso de expressões de consulta XPath.</span><span class="sxs-lookup"><span data-stu-id="915fb-104">You can supplement the standard XPath functions by implementing extension functions and variables for use by XPath query expressions.</span></span> <span data-ttu-id="915fb-105">O método de <xref:System.Xml.XPath.XPathExpression.SetContext%2A> pode aceitar um contexto definido pelo usuário derivado de <xref:System.Xml.Xsl.XsltContext>.</span><span class="sxs-lookup"><span data-stu-id="915fb-105">The <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method can accept a user defined context derived from <xref:System.Xml.Xsl.XsltContext>.</span></span> <span data-ttu-id="915fb-106">As funções definidas pelo usuário são resolvidas pelo contexto personalizado.</span><span class="sxs-lookup"><span data-stu-id="915fb-106">User defined functions are resolved by the custom context.</span></span>  
  
 <span data-ttu-id="915fb-107">Funções e variáveis de extensão podem ser úteis em prevenção de ataques de injeção XML.</span><span class="sxs-lookup"><span data-stu-id="915fb-107">Extension functions and variables can be useful in prevention of XML injection attacks.</span></span> <span data-ttu-id="915fb-108">Na entrada do usuário desses cenários é atribuído a variáveis personalizados e processado por funções de extensão, não como entrada raw concatenada com instruções de processamento.</span><span class="sxs-lookup"><span data-stu-id="915fb-108">In these scenarios user input is assigned to custom variables and processed by extension functions, not as raw input concatenated with processing instructions.</span></span> <span data-ttu-id="915fb-109">Funções e variáveis de extensão contêm a entrada do usuário para que funciona somente em dados XML como destinada pelo designer.</span><span class="sxs-lookup"><span data-stu-id="915fb-109">Extension functions and variables contain user input so that it only acts on XML data as intended by the designer.</span></span>  
  
 <span data-ttu-id="915fb-110">Para usar extensões você implementa uma classe personalizada de <xref:System.Xml.Xsl.XsltContext> junto com as interfaces <xref:System.Xml.Xsl.IXsltContextFunction> e <xref:System.Xml.Xsl.IXsltContextVariable> que suportam funções e variáveis de extensão.</span><span class="sxs-lookup"><span data-stu-id="915fb-110">To use extensions you implement a custom <xref:System.Xml.Xsl.XsltContext> class along with the interfaces <xref:System.Xml.Xsl.IXsltContextFunction> and <xref:System.Xml.Xsl.IXsltContextVariable> that support extension functions and variables.</span></span> <span data-ttu-id="915fb-111"><xref:System.Xml.XPath.XPathExpression> adiciona a entrada do usuário com seu <xref:System.Xml.Xsl.XsltArgumentList> a <xref:System.Xml.Xsl.XsltContext>personalizado.</span><span class="sxs-lookup"><span data-stu-id="915fb-111">An <xref:System.Xml.XPath.XPathExpression> adds user input with its <xref:System.Xml.Xsl.XsltArgumentList> to the custom <xref:System.Xml.Xsl.XsltContext>.</span></span>  
  
 <span data-ttu-id="915fb-112"><xref:System.Xml.XPath.XPathExpression> representa uma consulta compilado que <xref:System.Xml.XPath.XPathNavigator> usa para localizar e processa os nós identificados pela expressão.</span><span class="sxs-lookup"><span data-stu-id="915fb-112">The <xref:System.Xml.XPath.XPathExpression> represents a compiled query that <xref:System.Xml.XPath.XPathNavigator> uses to find and process the nodes identified by the expression.</span></span>  
  
 <span data-ttu-id="915fb-113">A implementação da seguir mostra de uma classe personalizada de contexto derivada de <xref:System.Xml.Xsl.XsltContext>.</span><span class="sxs-lookup"><span data-stu-id="915fb-113">The following example shows implementation of a custom context class derived from <xref:System.Xml.Xsl.XsltContext>.</span></span> <span data-ttu-id="915fb-114">Comentários no código a seguir descrevem membros de classe e seu uso em funções personalizados.</span><span class="sxs-lookup"><span data-stu-id="915fb-114">Comments in the code describe class members and their use in custom functions.</span></span> <span data-ttu-id="915fb-115">As implementações de função e de variável e um aplicativo de exemplo que usa essas implementações seguem este segmento de código.</span><span class="sxs-lookup"><span data-stu-id="915fb-115">Function and variable implementations and a sample application that uses these implementations follow this code segment.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#2](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#2)]
 [!code-vb[XPathExtensionFunctions#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#2)]  
  
 <span data-ttu-id="915fb-116">O código a seguir implementa <xref:System.Xml.Xsl.IXsltContextFunction>.</span><span class="sxs-lookup"><span data-stu-id="915fb-116">The following code implements <xref:System.Xml.Xsl.IXsltContextFunction>.</span></span> <span data-ttu-id="915fb-117">A classe que implementa resoluções de <xref:System.Xml.Xsl.IXsltContextFunction> e executa funções definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="915fb-117">The class that implements <xref:System.Xml.Xsl.IXsltContextFunction> resolves and executes user-defined functions.</span></span> <span data-ttu-id="915fb-118">Este exemplo usa a função identificada pela declaração: `private int CountChar(string title, char charTocount)`.</span><span class="sxs-lookup"><span data-stu-id="915fb-118">This example uses the function identified by the declaration: `private int CountChar(string title, char charTocount)`.</span></span>  
  
 <span data-ttu-id="915fb-119">Comentários de código a seguir descrevem membros de classe.</span><span class="sxs-lookup"><span data-stu-id="915fb-119">Code comments describe class members.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#3](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#3)]
 [!code-vb[XPathExtensionFunctions#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#3)]  
  
 <span data-ttu-id="915fb-120">O código a seguir implementa <xref:System.Xml.Xsl.IXsltContextVariable>.</span><span class="sxs-lookup"><span data-stu-id="915fb-120">The following code implements <xref:System.Xml.Xsl.IXsltContextVariable>.</span></span> <span data-ttu-id="915fb-121">Essa classe resolve referências a variáveis definidas pelo usuário em expressões de consulta XPath em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="915fb-121">This class resolves references to user-defined variables in XPath query expressions at run time.</span></span> <span data-ttu-id="915fb-122">Uma instância dessa classe é criada e retornada pelo método substituído de <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> de classe personalizada de <xref:System.Xml.Xsl.XsltContext> .</span><span class="sxs-lookup"><span data-stu-id="915fb-122">An instance of this class is created and returned by the overridden <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> method of the custom <xref:System.Xml.Xsl.XsltContext> class.</span></span>  
  
 <span data-ttu-id="915fb-123">Comentários de código a seguir descrevem os membros de classe.</span><span class="sxs-lookup"><span data-stu-id="915fb-123">Code comments describe the class members.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#4](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#4)]
 [!code-vb[XPathExtensionFunctions#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#4)]  
  
 <span data-ttu-id="915fb-124">Com definições de classe anteriores no escopo, o código a seguir usa a função personalizado para contar caracteres em elementos de documento de `Tasks.xml` .</span><span class="sxs-lookup"><span data-stu-id="915fb-124">With the previous class definitions in scope, the following code uses the custom function to count characters in the elements of the `Tasks.xml` document.</span></span> <span data-ttu-id="915fb-125">Comentários no código descrevem o código que cria a função personalizado e para executar contra o documento de `Tasks.xml` .</span><span class="sxs-lookup"><span data-stu-id="915fb-125">Comments in the code describe the code that compiles the custom function and runs it against the `Tasks.xml` document.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#1](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#1)]
 [!code-vb[XPathExtensionFunctions#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#1)]  
  
 <span data-ttu-id="915fb-126">Este exemplo usa os seguintes dados XML.</span><span class="sxs-lookup"><span data-stu-id="915fb-126">This example uses the following XML data.</span></span>  
  
 [!code-xml[XPathExtensionFunctions#5](../../../../samples/snippets/xml/VS_Snippets_Data/xpathextensionfunctions/XML/tasks.xml#5)]
