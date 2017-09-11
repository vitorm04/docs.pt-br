---
title: "Estrutura do programa e convenções de código (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- coding conventions
- Visual Basic code, coding conventions
- coding conventions, Visual Basic
- programs, structure
- program structure
- naming conventions, Visual Basic
- best practices, coding conventions
- conventions, Visual Basic coding
- Visual Basic code
- programming, Visual Basic coding conventions
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c3a091d64b3c55ad3f1291a635fd499da2dacdc8
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="fdcd3-102">Estrutura do programa e convenções de código (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fdcd3-102">Program Structure and Code Conventions (Visual Basic)</span></span>
<span data-ttu-id="fdcd3-103">Esta seção apresenta o típico [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] estrutura do programa, fornece uma simples [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] de programa "Hello, World" e discute [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] convenções de código.</span><span class="sxs-lookup"><span data-stu-id="fdcd3-103">This section introduces the typical [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program structure, provides a simple [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program, "Hello, World", and discusses [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code conventions.</span></span> <span data-ttu-id="fdcd3-104">Convenções de código são sugestões que o foco não na lógica do programa, mas em sua estrutura física e aparência.</span><span class="sxs-lookup"><span data-stu-id="fdcd3-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="fdcd3-105">Depois delas torna seu código mais fácil de ler, compreender e manter.</span><span class="sxs-lookup"><span data-stu-id="fdcd3-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="fdcd3-106">Convenções de código podem incluir, entre outros:</span><span class="sxs-lookup"><span data-stu-id="fdcd3-106">Code conventions can include, among others:</span></span>  
  
-   <span data-ttu-id="fdcd3-107">Formatos padronizados para rotular e comentando o código.</span><span class="sxs-lookup"><span data-stu-id="fdcd3-107">Standardized formats for labeling and commenting code.</span></span>  
  
-   <span data-ttu-id="fdcd3-108">Diretrizes para espaçamento, formatação e recuo do código.</span><span class="sxs-lookup"><span data-stu-id="fdcd3-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
-   <span data-ttu-id="fdcd3-109">Convenções de nomenclatura para objetos, variáveis e procedimentos.</span><span class="sxs-lookup"><span data-stu-id="fdcd3-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="fdcd3-110">Os tópicos a seguir apresentam um conjunto de diretrizes para de programação [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programas, junto com exemplos de uso de BOM.</span><span class="sxs-lookup"><span data-stu-id="fdcd3-110">The following topics present a set of programming guidelines for [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fdcd3-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="fdcd3-111">In This Section</span></span>  
 [<span data-ttu-id="fdcd3-112">Estrutura de um programa Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fdcd3-112">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="fdcd3-113">Fornece uma visão geral dos elementos que compõem um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programa.</span><span class="sxs-lookup"><span data-stu-id="fdcd3-113">Provides an overview of the elements that make up a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 [<span data-ttu-id="fdcd3-114">Procedimento principal no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fdcd3-114">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 <span data-ttu-id="fdcd3-115">Descreve o procedimento que serve como o início do ponto e controle geral para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fdcd3-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="fdcd3-116">Referências e a Instrução Imports</span><span class="sxs-lookup"><span data-stu-id="fdcd3-116">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 <span data-ttu-id="fdcd3-117">Discute como fazer referência a objetos em outros assemblies.</span><span class="sxs-lookup"><span data-stu-id="fdcd3-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="fdcd3-118">Namespaces no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fdcd3-118">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 <span data-ttu-id="fdcd3-119">Descreve como namespaces organizam objetos em assemblies.</span><span class="sxs-lookup"><span data-stu-id="fdcd3-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="fdcd3-120">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fdcd3-120">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 <span data-ttu-id="fdcd3-121">Inclui diretrizes gerais para nomear procedimentos, constantes, variáveis, argumentos e objetos.</span><span class="sxs-lookup"><span data-stu-id="fdcd3-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="fdcd3-122">Convenções de codificação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fdcd3-122">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 <span data-ttu-id="fdcd3-123">Revisa as diretrizes usadas no desenvolvimento de exemplos nesta documentação.</span><span class="sxs-lookup"><span data-stu-id="fdcd3-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="fdcd3-124">Compilação Condicional</span><span class="sxs-lookup"><span data-stu-id="fdcd3-124">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="fdcd3-125">Descreve como compilar específicos blocos de código seletivamente ao direcionar o compilador ignorar outros.</span><span class="sxs-lookup"><span data-stu-id="fdcd3-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="fdcd3-126">Como quebrar e combinar instruções no código</span><span class="sxs-lookup"><span data-stu-id="fdcd3-126">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="fdcd3-127">Mostra como dividir instruções longas em várias linhas e combinar instruções curtas em uma linha.</span><span class="sxs-lookup"><span data-stu-id="fdcd3-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="fdcd3-128">Como recolher e ocultar seções do código</span><span class="sxs-lookup"><span data-stu-id="fdcd3-128">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="fdcd3-129">Mostra como recolher e ocultar seções de código de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="fdcd3-129">Shows how to collapse and hide sections of code in the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code editor.</span></span>  
  
 [<span data-ttu-id="fdcd3-130">Como rotular instruções</span><span class="sxs-lookup"><span data-stu-id="fdcd3-130">How to: Label Statements</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 <span data-ttu-id="fdcd3-131">Mostra como marcar uma linha de código para identificá-lo para uso com instruções de como `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="fdcd3-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="fdcd3-132">Caracteres Especiais no Código</span><span class="sxs-lookup"><span data-stu-id="fdcd3-132">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 <span data-ttu-id="fdcd3-133">Mostra como e onde usar caracteres não alfabéticos e não-numéricos.</span><span class="sxs-lookup"><span data-stu-id="fdcd3-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="fdcd3-134">Comentários no Código</span><span class="sxs-lookup"><span data-stu-id="fdcd3-134">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 <span data-ttu-id="fdcd3-135">Descreve como adicionar comentários descritivos ao seu código.</span><span class="sxs-lookup"><span data-stu-id="fdcd3-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="fdcd3-136">Palavras-chave como Nomes de Elemento em Código</span><span class="sxs-lookup"><span data-stu-id="fdcd3-136">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 <span data-ttu-id="fdcd3-137">Descreve como usar colchetes (`[]`) para delimitar nomes de variáveis que são também [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] palavras-chave.</span><span class="sxs-lookup"><span data-stu-id="fdcd3-137">Describes how to use brackets (`[]`) to delimit variable names that are also [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] keywords.</span></span>  
  
 [<span data-ttu-id="fdcd3-138">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="fdcd3-138">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 <span data-ttu-id="fdcd3-139">Descreve várias maneiras de se referir a elementos de um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programa.</span><span class="sxs-lookup"><span data-stu-id="fdcd3-139">Describes various ways to refer to elements of a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 [<span data-ttu-id="fdcd3-140">Limitações do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fdcd3-140">Visual Basic Limitations</span></span>](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 <span data-ttu-id="fdcd3-141">Discute a remoção dos limites de codificação conhecidos em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="fdcd3-141">Discusses the removal of known coding limits within [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fdcd3-142">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="fdcd3-142">Related Sections</span></span>  
 [<span data-ttu-id="fdcd3-143">Convenções Tipográficas e de Código</span><span class="sxs-lookup"><span data-stu-id="fdcd3-143">Typographic and Code Conventions</span></span>](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="fdcd3-144">Fornece as convenções de codificação padrão para [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="fdcd3-144">Provides standard coding conventions for [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
 [<span data-ttu-id="fdcd3-145">Escrevendo código</span><span class="sxs-lookup"><span data-stu-id="fdcd3-145">Writing Code</span></span>](https://docs.microsoft.com/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="fdcd3-146">Descreve os recursos que tornam mais fácil para escrever e gerenciar seu código.</span><span class="sxs-lookup"><span data-stu-id="fdcd3-146">Describes features that make it easier for you to write and manage your code.</span></span>
