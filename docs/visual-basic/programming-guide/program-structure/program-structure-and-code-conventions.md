---
title: "Estrutura do programa e convenções de código (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b38ba9623a20dcd1be4bc96f4aff1eb646b0a053
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="10f38-102">Estrutura do programa e convenções de código (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10f38-102">Program Structure and Code Conventions (Visual Basic)</span></span>
<span data-ttu-id="10f38-103">Esta seção apresenta o típico [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] estrutura do programa, fornece um simples [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] de programa, "Olá, mundo" e discute [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] convenções de código.</span><span class="sxs-lookup"><span data-stu-id="10f38-103">This section introduces the typical [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program structure, provides a simple [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program, "Hello, World", and discusses [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code conventions.</span></span> <span data-ttu-id="10f38-104">Convenções de código são sugestões que se concentrar não na lógica de um programa, mas em sua estrutura física e aparência.</span><span class="sxs-lookup"><span data-stu-id="10f38-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="10f38-105">-Los a seguir torna o código mais fácil de ler, compreender e manter.</span><span class="sxs-lookup"><span data-stu-id="10f38-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="10f38-106">Convenções de código podem incluir, entre outros:</span><span class="sxs-lookup"><span data-stu-id="10f38-106">Code conventions can include, among others:</span></span>  
  
-   <span data-ttu-id="10f38-107">Formatos padronizados para rótulos e comentários de código.</span><span class="sxs-lookup"><span data-stu-id="10f38-107">Standardized formats for labeling and commenting code.</span></span>  
  
-   <span data-ttu-id="10f38-108">Diretrizes para espaçamento, formatação e recuo do código.</span><span class="sxs-lookup"><span data-stu-id="10f38-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
-   <span data-ttu-id="10f38-109">Convenções de nomenclatura de objetos, variáveis e procedimentos.</span><span class="sxs-lookup"><span data-stu-id="10f38-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="10f38-110">Os tópicos a seguir apresentam um conjunto de programação diretrizes para [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programas, junto com exemplos de uso BOM.</span><span class="sxs-lookup"><span data-stu-id="10f38-110">The following topics present a set of programming guidelines for [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="10f38-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="10f38-111">In This Section</span></span>  
 [<span data-ttu-id="10f38-112">Estrutura de um programa do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10f38-112">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="10f38-113">Fornece uma visão geral dos elementos que compõem um [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programa.</span><span class="sxs-lookup"><span data-stu-id="10f38-113">Provides an overview of the elements that make up a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 [<span data-ttu-id="10f38-114">Procedimento principal no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10f38-114">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 <span data-ttu-id="10f38-115">Descreve o procedimento que serve como a partir do ponto e controle geral para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="10f38-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="10f38-116">Referências e a Instrução Imports</span><span class="sxs-lookup"><span data-stu-id="10f38-116">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 <span data-ttu-id="10f38-117">Discute como fazer referência a objetos em outros assemblies.</span><span class="sxs-lookup"><span data-stu-id="10f38-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="10f38-118">Namespaces no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10f38-118">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 <span data-ttu-id="10f38-119">Descreve como namespaces organizar objetos em assemblies.</span><span class="sxs-lookup"><span data-stu-id="10f38-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="10f38-120">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10f38-120">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 <span data-ttu-id="10f38-121">Inclui diretrizes gerais para nomear procedimentos, constantes, variáveis, argumentos e objetos.</span><span class="sxs-lookup"><span data-stu-id="10f38-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="10f38-122">Convenções de codificação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10f38-122">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 <span data-ttu-id="10f38-123">Revisa as diretrizes usadas no desenvolvimento de exemplos nesta documentação.</span><span class="sxs-lookup"><span data-stu-id="10f38-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="10f38-124">Compilação Condicional</span><span class="sxs-lookup"><span data-stu-id="10f38-124">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="10f38-125">Descreve como compilar específicos blocos de código seletivamente ao direcionar o compilador ignorar a outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="10f38-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="10f38-126">Como quebrar e combinar instruções no código</span><span class="sxs-lookup"><span data-stu-id="10f38-126">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="10f38-127">Mostra como dividir instruções longo em várias linhas e combinar instruções curtas em uma linha.</span><span class="sxs-lookup"><span data-stu-id="10f38-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="10f38-128">Como recolher e ocultar seções do código</span><span class="sxs-lookup"><span data-stu-id="10f38-128">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="10f38-129">Mostra como recolher e ocultar seções de código no [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="10f38-129">Shows how to collapse and hide sections of code in the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code editor.</span></span>  
  
 [<span data-ttu-id="10f38-130">Como rotular instruções</span><span class="sxs-lookup"><span data-stu-id="10f38-130">How to: Label Statements</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 <span data-ttu-id="10f38-131">Mostra como marcar uma linha de código para identificá-lo para uso com instruções de como `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="10f38-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="10f38-132">Caracteres Especiais no Código</span><span class="sxs-lookup"><span data-stu-id="10f38-132">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 <span data-ttu-id="10f38-133">Mostra como e onde usar caracteres não alfabéticos e não-numéricos.</span><span class="sxs-lookup"><span data-stu-id="10f38-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="10f38-134">Comentários no Código</span><span class="sxs-lookup"><span data-stu-id="10f38-134">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 <span data-ttu-id="10f38-135">Descreve como adicionar comentários descritivos ao seu código.</span><span class="sxs-lookup"><span data-stu-id="10f38-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="10f38-136">Palavras-chave como Nomes de Elemento em Código</span><span class="sxs-lookup"><span data-stu-id="10f38-136">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 <span data-ttu-id="10f38-137">Descreve como usar colchetes (`[]`) para delimitar nomes de variáveis que são também [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] palavras-chave.</span><span class="sxs-lookup"><span data-stu-id="10f38-137">Describes how to use brackets (`[]`) to delimit variable names that are also [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] keywords.</span></span>  
  
 [<span data-ttu-id="10f38-138">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="10f38-138">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 <span data-ttu-id="10f38-139">Descreve várias formas para se referir a elementos de um [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programa.</span><span class="sxs-lookup"><span data-stu-id="10f38-139">Describes various ways to refer to elements of a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 [<span data-ttu-id="10f38-140">Limitações do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10f38-140">Visual Basic Limitations</span></span>](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 <span data-ttu-id="10f38-141">Discute a remoção dos limites conhecidos de codificação em [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="10f38-141">Discusses the removal of known coding limits within [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="10f38-142">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="10f38-142">Related Sections</span></span>  
 [<span data-ttu-id="10f38-143">Convenções Tipográficas e de Código</span><span class="sxs-lookup"><span data-stu-id="10f38-143">Typographic and Code Conventions</span></span>](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="10f38-144">Fornece as convenções de codificação padrão para [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="10f38-144">Provides standard coding conventions for [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 [<span data-ttu-id="10f38-145">Escrevendo código</span><span class="sxs-lookup"><span data-stu-id="10f38-145">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="10f38-146">Descreve recursos que tornam mais fácil para gravar e gerenciar seu código.</span><span class="sxs-lookup"><span data-stu-id="10f38-146">Describes features that make it easier for you to write and manage your code.</span></span>
