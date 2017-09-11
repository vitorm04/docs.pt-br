---
title: "Instrução Error | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.error
dev_langs:
- VB
helpviewer_keywords:
- Error statement, syntax
- Error statement
- Error keyword
- run-time errors, codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 7a88fe065aaf202067d52ca7640c2d098d9686d2
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="error-statement"></a><span data-ttu-id="f3782-102">Instrução Error</span><span class="sxs-lookup"><span data-stu-id="f3782-102">Error Statement</span></span>
<span data-ttu-id="f3782-103">Simula a ocorrência de um erro.</span><span class="sxs-lookup"><span data-stu-id="f3782-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3782-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3782-104">Syntax</span></span>  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="f3782-105">Partes</span><span class="sxs-lookup"><span data-stu-id="f3782-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="f3782-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="f3782-106">Required.</span></span> <span data-ttu-id="f3782-107">Pode ser qualquer número de erro válido.</span><span class="sxs-lookup"><span data-stu-id="f3782-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3782-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="f3782-108">Remarks</span></span>  
 <span data-ttu-id="f3782-109">O `Error` instrução é suportada para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="f3782-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="f3782-110">No novo código, especialmente ao criar objetos, use o `Err` do objeto `Raise` método para gerar erros de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f3782-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="f3782-111">Se `errornumber` for definida, o `Error` instrução chama o manipulador de erro após as propriedades do `Err` objeto são atribuídos os seguintes valores padrão:</span><span class="sxs-lookup"><span data-stu-id="f3782-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="f3782-112">Propriedade</span><span class="sxs-lookup"><span data-stu-id="f3782-112">Property</span></span>|<span data-ttu-id="f3782-113">Valor</span><span class="sxs-lookup"><span data-stu-id="f3782-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="f3782-114">Valor especificado como argumento para `Error` instrução.</span><span class="sxs-lookup"><span data-stu-id="f3782-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="f3782-115">Pode ser qualquer número de erro válido.</span><span class="sxs-lookup"><span data-stu-id="f3782-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="f3782-116">Nome do projeto atual do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f3782-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="f3782-117">Expressão correspondente para o valor de retorno de cadeia de caracteres de `Error` função especificado `Number`, se houver essa cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f3782-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="f3782-118">Se a cadeia de caracteres não existir, `Description` contém uma cadeia de caracteres de comprimento zero ("").</span><span class="sxs-lookup"><span data-stu-id="f3782-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="f3782-119">A unidade totalmente qualificada, o caminho e o nome do arquivo de Ajuda do Visual Basic apropriado.</span><span class="sxs-lookup"><span data-stu-id="f3782-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="f3782-120">ID de contexto para o erro correspondente de arquivos de ajuda Visual Basic a `Number` propriedade.</span><span class="sxs-lookup"><span data-stu-id="f3782-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="f3782-121">Zero.</span><span class="sxs-lookup"><span data-stu-id="f3782-121">Zero.</span></span>|  
  
 <span data-ttu-id="f3782-122">Se nenhum manipulador de erro existe, ou se nenhum está ativado, uma mensagem de erro é criada e exibida a partir de `Err` propriedades do objeto.</span><span class="sxs-lookup"><span data-stu-id="f3782-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3782-123">Alguns aplicativos de host do Visual Basic não podem criar objetos.</span><span class="sxs-lookup"><span data-stu-id="f3782-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="f3782-124">Consulte a documentação do aplicativo host para determinar se ele pode criar classes e objetos.</span><span class="sxs-lookup"><span data-stu-id="f3782-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3782-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f3782-125">Example</span></span>  
 <span data-ttu-id="f3782-126">Este exemplo usa o `Error` instrução para gerar o erro número 11.</span><span class="sxs-lookup"><span data-stu-id="f3782-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="f3782-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f3782-127">Requirements</span></span>  
 <span data-ttu-id="f3782-128">**Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="f3782-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="f3782-129">**Assembly:** biblioteca de tempo de execução do Visual Basic (em Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="f3782-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3782-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3782-130">See Also</span></span>  
 <span data-ttu-id="f3782-131"><xref:Microsoft.VisualBasic.ErrObject.Clear%2A></xref:Microsoft.VisualBasic.ErrObject.Clear%2A></span><span class="sxs-lookup"><span data-stu-id="f3782-131"><xref:Microsoft.VisualBasic.ErrObject.Clear%2A></span></span>   
 <span data-ttu-id="f3782-132"><xref:Microsoft.VisualBasic.Information.Err%2A></xref:Microsoft.VisualBasic.Information.Err%2A></span><span class="sxs-lookup"><span data-stu-id="f3782-132"><xref:Microsoft.VisualBasic.Information.Err%2A></span></span>   
 <span data-ttu-id="f3782-133"><xref:Microsoft.VisualBasic.ErrObject.Raise%2A></xref:Microsoft.VisualBasic.ErrObject.Raise%2A></span><span class="sxs-lookup"><span data-stu-id="f3782-133"><xref:Microsoft.VisualBasic.ErrObject.Raise%2A></span></span>   
<span data-ttu-id="f3782-134"> [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md) </span><span class="sxs-lookup"><span data-stu-id="f3782-134"> [On Error Statement](../../../visual-basic/language-reference/statements/on-error-statement.md) </span></span>  
<span data-ttu-id="f3782-135"> [Instrução Resume](../../../visual-basic/language-reference/statements/resume-statement.md) </span><span class="sxs-lookup"><span data-stu-id="f3782-135"> [Resume Statement](../../../visual-basic/language-reference/statements/resume-statement.md) </span></span>  
<span data-ttu-id="f3782-136"> [Mensagens de Erro](../../../visual-basic/language-reference/error-messages/index.md)</span><span class="sxs-lookup"><span data-stu-id="f3782-136"> [Error Messages](../../../visual-basic/language-reference/error-messages/index.md)</span></span>
