---
title: Diretivas (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: 38d54feae5cf7bf41a825d1f6000811e2b56f319
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43736601"
---
# <a name="directives-visual-basic"></a>Diretivas (Visual Basic)
Os tópicos desta seção documentam as diretivas de compilador de código de origem do Visual Basic.  
  
## <a name="in-this-section"></a>Nesta seção  
 [# Diretiva const](../../../visual-basic/language-reference/directives/const-directive.md) – definir uma constante de compilação  
  
 [Diretiva #ExternalSource](../../../visual-basic/language-reference/directives/externalsource-directive.md) – indica um mapeamento entre as linhas de origem e o texto externo à origem  
  
 [#If... ... Then diretivas #Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md) – compilar blocos de código selecionados  
  
 [Diretiva #Region](../../../visual-basic/language-reference/directives/region-directive.md) - recolher e ocultar seções do código no editor do Visual Studio  
  
 **#Disable, #Enable** - - desabilitar e habilitar avisos específicos para regiões de código.  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 Você pode desabilitar e habilitar uma lista separada por vírgulas dos códigos de aviso também.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md)  
  
 [Visual Basic](../../../visual-basic/index.md)
