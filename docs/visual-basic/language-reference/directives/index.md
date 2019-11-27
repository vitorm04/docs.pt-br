---
title: Diretivas
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: d76e10ad5ce8ad3accdc84f97146e0816048d8f3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343798"
---
# <a name="directives-visual-basic"></a><span data-ttu-id="c5b40-102">Diretivas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5b40-102">Directives (Visual Basic)</span></span>

<span data-ttu-id="c5b40-103">Os tópicos nesta seção documentam as diretivas Visual Basic do compilador do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="c5b40-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c5b40-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c5b40-104">In This Section</span></span>  

 <span data-ttu-id="c5b40-105">[Diretiva #Const](../../../visual-basic/language-reference/directives/const-directive.md) – definir uma constante do compilador</span><span class="sxs-lookup"><span data-stu-id="c5b40-105">[#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="c5b40-106">[Diretiva #ExternalSource](../../../visual-basic/language-reference/directives/externalsource-directive.md) --indica um mapeamento entre linhas de origem e texto externo à origem</span><span class="sxs-lookup"><span data-stu-id="c5b40-106">[#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="c5b40-107">[#If... Then... #Else diretivas](../../../visual-basic/language-reference/directives/if-then-else-directives.md) – compilar blocos de código selecionados</span><span class="sxs-lookup"><span data-stu-id="c5b40-107">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="c5b40-108">[Diretiva #Region](../../../visual-basic/language-reference/directives/region-directive.md) – recolher e ocultar seções de código no editor do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c5b40-108">[#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="c5b40-109">**#Disable, #Enable** --desabilitar e habilitar avisos específicos para regiões de código.</span><span class="sxs-lookup"><span data-stu-id="c5b40-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="c5b40-110">Você também pode desabilitar e habilitar uma lista separada por vírgulas de códigos de aviso.</span><span class="sxs-lookup"><span data-stu-id="c5b40-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c5b40-111">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="c5b40-111">Related Sections</span></span>  

 [<span data-ttu-id="c5b40-112">Referência da linguagem Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c5b40-112">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
  
 [<span data-ttu-id="c5b40-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c5b40-113">Visual Basic</span></span>](../../../visual-basic/index.md)
