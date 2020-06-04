---
title: Diretivas
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: b5fcf3cb8801bc99dd2096c28cc41ebefeb34592
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409992"
---
# <a name="directives-visual-basic"></a><span data-ttu-id="a57ff-102">Diretivas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a57ff-102">Directives (Visual Basic)</span></span>

<span data-ttu-id="a57ff-103">Os tópicos nesta seção documentam as diretivas Visual Basic do compilador do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="a57ff-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a57ff-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="a57ff-104">In This Section</span></span>  

 <span data-ttu-id="a57ff-105">[Diretiva #Const](const-directive.md) – definir uma constante do compilador</span><span class="sxs-lookup"><span data-stu-id="a57ff-105">[#Const Directive](const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="a57ff-106">[Diretiva #ExternalSource](externalsource-directive.md) --indica um mapeamento entre linhas de origem e texto externo à origem</span><span class="sxs-lookup"><span data-stu-id="a57ff-106">[#ExternalSource Directive](externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="a57ff-107">[#If... Then... #Else diretivas](if-then-else-directives.md) – compilar blocos de código selecionados</span><span class="sxs-lookup"><span data-stu-id="a57ff-107">[#If...Then...#Else Directives](if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="a57ff-108">[Diretiva #Region](region-directive.md) – recolher e ocultar seções de código no editor do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a57ff-108">[#Region Directive](region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="a57ff-109">**#Disable, #Enable** --desabilitar e habilitar avisos específicos para regiões de código.</span><span class="sxs-lookup"><span data-stu-id="a57ff-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="a57ff-110">Você também pode desabilitar e habilitar uma lista separada por vírgulas de códigos de aviso.</span><span class="sxs-lookup"><span data-stu-id="a57ff-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a57ff-111">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="a57ff-111">Related Sections</span></span>  

 [<span data-ttu-id="a57ff-112">Referência de linguagem de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a57ff-112">Visual Basic Language Reference</span></span>](../index.md)  
  