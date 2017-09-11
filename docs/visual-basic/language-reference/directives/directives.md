---
title: Diretivas (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
caps.latest.revision: 9
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: d499240c4ccfebd2cc2324b77a67112094913a40
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="directives-visual-basic"></a><span data-ttu-id="d0240-102">Diretivas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0240-102">Directives (Visual Basic)</span></span>
<span data-ttu-id="d0240-103">Os tópicos nesta seção documentam as diretivas de compilador de código de origem do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d0240-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d0240-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="d0240-104">In This Section</span></span>  
 <span data-ttu-id="d0240-105">[# Diretiva const](../../../visual-basic/language-reference/directives/const-directive.md) -definir uma constante de compilação</span><span class="sxs-lookup"><span data-stu-id="d0240-105">[#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="d0240-106">[Diretiva #ExternalSource](../../../visual-basic/language-reference/directives/externalsource-directive.md) – indica um mapeamento entre linhas de código-fonte e texto externo a fonte</span><span class="sxs-lookup"><span data-stu-id="d0240-106">[#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="d0240-107">[#If... Then... #Else diretivas](../../../visual-basic/language-reference/directives/if-then-else-directives.md) – compilar blocos de código selecionados</span><span class="sxs-lookup"><span data-stu-id="d0240-107">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="d0240-108">[Diretiva #Region](../../../visual-basic/language-reference/directives/region-directive.md) - recolher e ocultar seções de código no editor do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d0240-108">[#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="d0240-109">**#Disable, #Enable** - - desabilitar e habilitar avisos específicos para regiões de código.</span><span class="sxs-lookup"><span data-stu-id="d0240-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="d0240-110">Você pode desabilitar e habilitar uma lista separada por vírgulas dos códigos de aviso demais.</span><span class="sxs-lookup"><span data-stu-id="d0240-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d0240-111">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="d0240-111">Related Sections</span></span>  
 [<span data-ttu-id="d0240-112">Referência da linguagem Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d0240-112">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
  
 [<span data-ttu-id="d0240-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d0240-113">Visual Basic</span></span>](../../../visual-basic/index.md)

