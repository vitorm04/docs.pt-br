---
title: Diretivas (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: 38d54feae5cf7bf41a825d1f6000811e2b56f319
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44187267"
---
# <a name="directives-visual-basic"></a><span data-ttu-id="81ff1-102">Diretivas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81ff1-102">Directives (Visual Basic)</span></span>
<span data-ttu-id="81ff1-103">Os tópicos desta seção documentam as diretivas de compilador de código de origem do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="81ff1-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="81ff1-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="81ff1-104">In This Section</span></span>  
 <span data-ttu-id="81ff1-105">[# Diretiva const](../../../visual-basic/language-reference/directives/const-directive.md) – definir uma constante de compilação</span><span class="sxs-lookup"><span data-stu-id="81ff1-105">[#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="81ff1-106">[Diretiva #ExternalSource](../../../visual-basic/language-reference/directives/externalsource-directive.md) – indica um mapeamento entre as linhas de origem e o texto externo à origem</span><span class="sxs-lookup"><span data-stu-id="81ff1-106">[#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="81ff1-107">[#If... ... Then diretivas #Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md) – compilar blocos de código selecionados</span><span class="sxs-lookup"><span data-stu-id="81ff1-107">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="81ff1-108">[Diretiva #Region](../../../visual-basic/language-reference/directives/region-directive.md) - recolher e ocultar seções do código no editor do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="81ff1-108">[#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="81ff1-109">**#Disable, #Enable** - - desabilitar e habilitar avisos específicos para regiões de código.</span><span class="sxs-lookup"><span data-stu-id="81ff1-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="81ff1-110">Você pode desabilitar e habilitar uma lista separada por vírgulas dos códigos de aviso também.</span><span class="sxs-lookup"><span data-stu-id="81ff1-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="81ff1-111">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="81ff1-111">Related Sections</span></span>  
 [<span data-ttu-id="81ff1-112">Referência da linguagem Visual Basic</span><span class="sxs-lookup"><span data-stu-id="81ff1-112">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
  
 [<span data-ttu-id="81ff1-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="81ff1-113">Visual Basic</span></span>](../../../visual-basic/index.md)
