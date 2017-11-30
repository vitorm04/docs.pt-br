---
title: Classe Exception e suas propriedades
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 253a9846e484aa4e54c3433b0bbc8623519bbb7e
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2017
---
# <a name="exception-class-and-properties"></a><span data-ttu-id="964e6-102">Classe e propriedades da exceção</span><span class="sxs-lookup"><span data-stu-id="964e6-102">Exception class and properties</span></span>

<span data-ttu-id="964e6-103">A classe <xref:System.Exception> é a classe base da qual as exceções herdam.</span><span class="sxs-lookup"><span data-stu-id="964e6-103">The <xref:System.Exception> class is the base class from which exceptions inherit.</span></span> <span data-ttu-id="964e6-104">Por exemplo, a hierarquia de classe <xref:System.InvalidCastException> é como se segue:</span><span class="sxs-lookup"><span data-stu-id="964e6-104">For example, the <xref:System.InvalidCastException> class hierarchy is as follows:</span></span>

```
Object
  Exception
    SystemException
       InvalidCastException
```

<span data-ttu-id="964e6-105">A classe <xref:System.Exception> tem as propriedades a seguir, que ajudam a facilitar o entendimento de uma exceção.</span><span class="sxs-lookup"><span data-stu-id="964e6-105">The <xref:System.Exception> class has the following properties that help make understanding an exception easier.</span></span>

| <span data-ttu-id="964e6-106">Nome da Propriedade</span><span class="sxs-lookup"><span data-stu-id="964e6-106">Property Name</span></span> | <span data-ttu-id="964e6-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="964e6-107">Description</span></span> |
| ------------- | ----------- |
| <xref:System.Exception.Data> | <span data-ttu-id="964e6-108">Um <xref:System.Collections.IDictionary> que contém dados arbitrários em pares chave-valor.</span><span class="sxs-lookup"><span data-stu-id="964e6-108">An <xref:System.Collections.IDictionary> that holds arbitrary data in key-value pairs.</span></span> |
| <xref:System.Exception.HelpLink> | <span data-ttu-id="964e6-109">Pode conter uma URL (ou URN) para um arquivo de ajuda que fornece informações abrangentes sobre a causa de uma exceção.</span><span class="sxs-lookup"><span data-stu-id="964e6-109">Can hold a URL (or URN) to a help file that provides extensive information about the cause of an exception.</span></span> |
| <xref:System.Exception.InnerException> | <span data-ttu-id="964e6-110">Essa propriedade pode ser usada para criar e manter uma série de exceções durante o tratamento de exceção.</span><span class="sxs-lookup"><span data-stu-id="964e6-110">This property can be used to create and preserve a series of exceptions during exception handling.</span></span> <span data-ttu-id="964e6-111">Você pode usá-lo para criar uma nova exceção contendo exceções previamente capturadas.</span><span class="sxs-lookup"><span data-stu-id="964e6-111">You can use it to create a new exception that contains previously caught exceptions.</span></span> <span data-ttu-id="964e6-112">A exceção original pode ser capturada pela segunda exceção na propriedade <xref:System.Exception.InnerException>, permitindo que o código que trata da segunda exceção examine as informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="964e6-112">The original exception can be captured by the second exception in the <xref:System.Exception.InnerException> property, allowing code that handles the second exception to examine the additional information.</span></span> <span data-ttu-id="964e6-113">Por exemplo, suponha que você tem um método que recebe um argumento que está formatado de modo inadequado.</span><span class="sxs-lookup"><span data-stu-id="964e6-113">For example, suppose you have a method that receives an argument that's improperly formatted.</span></span>  <span data-ttu-id="964e6-114">O código tenta ler o argumento, mas uma exceção é gerada.</span><span class="sxs-lookup"><span data-stu-id="964e6-114">The code tries to read the argument, but an exception is thrown.</span></span> <span data-ttu-id="964e6-115">O método captura a exceção e gera um <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="964e6-115">The method catches the exception and throws a <xref:System.FormatException>.</span></span> <span data-ttu-id="964e6-116">Para melhorar a capacidade do chamador para determinar o motivo pelo qual que uma exceção é gerada, às vezes é desejável que um método capture uma exceção gerada por uma rotina auxiliar e, em seguida, gere uma exceção mais indicativa do erro que ocorreu.</span><span class="sxs-lookup"><span data-stu-id="964e6-116">To improve the caller's ability to determine the reason an exception is thrown, it is sometimes desirable for a method to catch an exception thrown by a helper routine and then throw an exception more indicative of the error that has occurred.</span></span> <span data-ttu-id="964e6-117">Uma exceção mais nova e mais significativa pode ser criada, na qual a referência à exceção interna pode ser definida para a exceção original.</span><span class="sxs-lookup"><span data-stu-id="964e6-117">A new and more meaningful exception can be created, where the inner exception reference can be set to the original exception.</span></span> <span data-ttu-id="964e6-118">Essa exceção mais significativa pode, em seguida, ser gerada para o chamador.</span><span class="sxs-lookup"><span data-stu-id="964e6-118">This more meaningful exception can then be thrown to the caller.</span></span> <span data-ttu-id="964e6-119">Observe que com essa funcionalidade você pode criar uma série de exceções vinculadas que termina com a primeira exceção gerada.</span><span class="sxs-lookup"><span data-stu-id="964e6-119">Note that with this functionality, you can create a series of linked exceptions that ends with the exception that was thrown first.</span></span> |
| <xref:System.Exception.Message> | <span data-ttu-id="964e6-120">Fornece detalhes sobre a causa de uma exceção.</span><span class="sxs-lookup"><span data-stu-id="964e6-120">Provides details about the cause of an exception.</span></span>
| <xref:System.Exception.Source> | <span data-ttu-id="964e6-121">Obtém ou define o nome do aplicativo ou objeto que causa o erro.</span><span class="sxs-lookup"><span data-stu-id="964e6-121">Gets or sets the name of the application or the object that causes the error.</span></span> |
| <xref:System.Exception.StackTrace>| <span data-ttu-id="964e6-122">Contém um rastreamento de pilha que pode ser usado para determinar onde um erro ocorreu.</span><span class="sxs-lookup"><span data-stu-id="964e6-122">Contains a stack trace that can be used to determine where an error occurred.</span></span> <span data-ttu-id="964e6-123">O rastreamento de pilha inclui o nome do arquivo de origem e o número de linha de programa se informações de depuração estiverem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="964e6-123">The stack trace includes the source file name and program line number if debugging information is available.</span></span> |

<span data-ttu-id="964e6-124">A maioria das classes que herdam de <xref:System.Exception> não implementa membros adicionais nem fornece funcionalidade adicional; apenas herdam de <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="964e6-124">Most of the classes that inherit from <xref:System.Exception> do not implement additional members or provide additional functionality; they simply inherit from <xref:System.Exception>.</span></span> <span data-ttu-id="964e6-125">Portanto, as informações mais importantes para uma exceção podem ser encontradas na hierarquia de classes de exceção, no nome da exceção e nas informações contidas na exceção.</span><span class="sxs-lookup"><span data-stu-id="964e6-125">Therefore, the most important information for an exception can be found in the hierarchy of exception classes, the exception name, and the information contained in the exception.</span></span>

<span data-ttu-id="964e6-126">É recomendável que você gera e captura apenas objetos que derivam de <xref:System.Exception>, mas você pode lançar qualquer objeto que deriva o <xref:System.Object> classe como uma exceção.</span><span class="sxs-lookup"><span data-stu-id="964e6-126">We recommend that you throw and catch only objects that derive from <xref:System.Exception>, but you can throw any object that derives from the <xref:System.Object> class as an exception.</span></span> <span data-ttu-id="964e6-127">Observe que nem todas as linguagens dão suporte à geração e captura de objetos que não derivam de <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="964e6-127">Note that not all languages support throwing and catching objects that do not derive from <xref:System.Exception>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="964e6-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="964e6-128">See Also</span></span>  
[<span data-ttu-id="964e6-129">Exceções</span><span class="sxs-lookup"><span data-stu-id="964e6-129">Exceptions</span></span>](index.md)
