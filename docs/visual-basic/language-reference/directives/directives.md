---
title: Diretivas (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: 38d54feae5cf7bf41a825d1f6000811e2b56f319
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584631"
---
# <a name="directives-visual-basic"></a>Diretivas (Visual Basic)
Os tópicos nesta seção documentam as diretivas de compilador de código de origem do Visual Basic.  
  
## <a name="in-this-section"></a>Nesta seção  
 [# Diretiva const](../../../visual-basic/language-reference/directives/const-directive.md) -definir uma constante de compilação  
  
 [Diretiva #ExternalSource](../../../visual-basic/language-reference/directives/externalsource-directive.md) – indica um mapeamento entre as linhas de origem e externo para a fonte do texto  
  
 [#If... Then... #Else diretivas](../../../visual-basic/language-reference/directives/if-then-else-directives.md) -compilar blocos de código selecionados  
  
 [Diretiva #Region](../../../visual-basic/language-reference/directives/region-directive.md) - recolher e ocultar seções do código no editor do Visual Studio  
  
 **#Disable, #Enable** - desabilitar e habilitar avisos específicos para regiões de código.  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 Você pode desabilitar e habilitar uma lista separada por vírgulas dos códigos de aviso muito.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md)  
  
 [Visual Basic](../../../visual-basic/index.md)
