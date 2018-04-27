---
title: Estrutura do programa e convenções de código (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- coding conventions
- Visual Basic code, coding conventions
- coding conventions [Visual Basic], Visual Basic
- programs [Visual Basic], structure
- program structure [Visual Basic]
- naming conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- Visual Basic code
- programming [Visual Basic], Visual Basic coding conventions
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9980a815d83b21214f1be441d641c3da38c1b541
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="c8f61-102">Estrutura do programa e convenções de código (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8f61-102">Program Structure and Code Conventions (Visual Basic)</span></span>
<span data-ttu-id="c8f61-103">Esta seção apresenta a estrutura do programa Visual Basic típica, fornece um programa simple do Visual Basic, "Olá, mundo" e discute as convenções de código do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c8f61-103">This section introduces the typical Visual Basic program structure, provides a simple Visual Basic program, "Hello, World", and discusses Visual Basic code conventions.</span></span> <span data-ttu-id="c8f61-104">Convenções de código são sugestões que se concentrar não na lógica de um programa, mas em sua estrutura física e aparência.</span><span class="sxs-lookup"><span data-stu-id="c8f61-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="c8f61-105">-Los a seguir torna o código mais fácil de ler, compreender e manter.</span><span class="sxs-lookup"><span data-stu-id="c8f61-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="c8f61-106">Convenções de código podem incluir, entre outros:</span><span class="sxs-lookup"><span data-stu-id="c8f61-106">Code conventions can include, among others:</span></span>  
  
-   <span data-ttu-id="c8f61-107">Formatos padronizados para rótulos e comentários de código.</span><span class="sxs-lookup"><span data-stu-id="c8f61-107">Standardized formats for labeling and commenting code.</span></span>  
  
-   <span data-ttu-id="c8f61-108">Diretrizes para espaçamento, formatação e recuo do código.</span><span class="sxs-lookup"><span data-stu-id="c8f61-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
-   <span data-ttu-id="c8f61-109">Convenções de nomenclatura de objetos, variáveis e procedimentos.</span><span class="sxs-lookup"><span data-stu-id="c8f61-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="c8f61-110">Os tópicos a seguir apresentam um conjunto de diretrizes de programação para programas em Visual Basic, junto com exemplos de uso BOM.</span><span class="sxs-lookup"><span data-stu-id="c8f61-110">The following topics present a set of programming guidelines for Visual Basic programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c8f61-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c8f61-111">In This Section</span></span>  
 [<span data-ttu-id="c8f61-112">Estrutura de um programa do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c8f61-112">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="c8f61-113">Fornece uma visão geral dos elementos que compõem um programa Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c8f61-113">Provides an overview of the elements that make up a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="c8f61-114">Procedimento principal no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c8f61-114">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 <span data-ttu-id="c8f61-115">Descreve o procedimento que serve como a partir do ponto e controle geral para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8f61-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="c8f61-116">Referências e a Instrução Imports</span><span class="sxs-lookup"><span data-stu-id="c8f61-116">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 <span data-ttu-id="c8f61-117">Discute como fazer referência a objetos em outros assemblies.</span><span class="sxs-lookup"><span data-stu-id="c8f61-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="c8f61-118">Namespaces no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c8f61-118">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 <span data-ttu-id="c8f61-119">Descreve como namespaces organizar objetos em assemblies.</span><span class="sxs-lookup"><span data-stu-id="c8f61-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="c8f61-120">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c8f61-120">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 <span data-ttu-id="c8f61-121">Inclui diretrizes gerais para nomear procedimentos, constantes, variáveis, argumentos e objetos.</span><span class="sxs-lookup"><span data-stu-id="c8f61-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="c8f61-122">Convenções de codificação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c8f61-122">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 <span data-ttu-id="c8f61-123">Revisa as diretrizes usadas no desenvolvimento de exemplos nesta documentação.</span><span class="sxs-lookup"><span data-stu-id="c8f61-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="c8f61-124">Compilação Condicional</span><span class="sxs-lookup"><span data-stu-id="c8f61-124">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="c8f61-125">Descreve como compilar específicos blocos de código seletivamente ao direcionar o compilador ignorar a outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="c8f61-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="c8f61-126">Como quebrar e combinar instruções no código</span><span class="sxs-lookup"><span data-stu-id="c8f61-126">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="c8f61-127">Mostra como dividir instruções longo em várias linhas e combinar instruções curtas em uma linha.</span><span class="sxs-lookup"><span data-stu-id="c8f61-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="c8f61-128">Como recolher e ocultar seções do código</span><span class="sxs-lookup"><span data-stu-id="c8f61-128">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="c8f61-129">Mostra como recolher e ocultar seções de código do Visual Basic do editor de código.</span><span class="sxs-lookup"><span data-stu-id="c8f61-129">Shows how to collapse and hide sections of code in the Visual Basic code editor.</span></span>  
  
 [<span data-ttu-id="c8f61-130">Como rotular instruções</span><span class="sxs-lookup"><span data-stu-id="c8f61-130">How to: Label Statements</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 <span data-ttu-id="c8f61-131">Mostra como marcar uma linha de código para identificá-lo para uso com instruções de como `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="c8f61-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="c8f61-132">Caracteres Especiais no Código</span><span class="sxs-lookup"><span data-stu-id="c8f61-132">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 <span data-ttu-id="c8f61-133">Mostra como e onde usar caracteres não alfabéticos e não-numéricos.</span><span class="sxs-lookup"><span data-stu-id="c8f61-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="c8f61-134">Comentários no Código</span><span class="sxs-lookup"><span data-stu-id="c8f61-134">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 <span data-ttu-id="c8f61-135">Descreve como adicionar comentários descritivos ao seu código.</span><span class="sxs-lookup"><span data-stu-id="c8f61-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="c8f61-136">Palavras-chave como Nomes de Elemento em Código</span><span class="sxs-lookup"><span data-stu-id="c8f61-136">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 <span data-ttu-id="c8f61-137">Descreve como usar colchetes (`[]`) para delimitar nomes de variáveis que são também palavras-chave do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c8f61-137">Describes how to use brackets (`[]`) to delimit variable names that are also Visual Basic keywords.</span></span>  
  
 [<span data-ttu-id="c8f61-138">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="c8f61-138">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 <span data-ttu-id="c8f61-139">Descreve várias formas para se referir a elementos de um programa Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c8f61-139">Describes various ways to refer to elements of a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="c8f61-140">Limitações do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c8f61-140">Visual Basic Limitations</span></span>](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 <span data-ttu-id="c8f61-141">Discute a remoção dos limites conhecidos de codificação no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c8f61-141">Discusses the removal of known coding limits within Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c8f61-142">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="c8f61-142">Related Sections</span></span>  
 [<span data-ttu-id="c8f61-143">Convenções Tipográficas e de Código</span><span class="sxs-lookup"><span data-stu-id="c8f61-143">Typographic and Code Conventions</span></span>](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="c8f61-144">Fornece as convenções de codificação padrão para o Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c8f61-144">Provides standard coding conventions for Visual Basic.</span></span>  
  
 [<span data-ttu-id="c8f61-145">Escrevendo código</span><span class="sxs-lookup"><span data-stu-id="c8f61-145">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="c8f61-146">Descreve recursos que tornam mais fácil para gravar e gerenciar seu código.</span><span class="sxs-lookup"><span data-stu-id="c8f61-146">Describes features that make it easier for you to write and manage your code.</span></span>
