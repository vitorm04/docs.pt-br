---
title: Diretivas (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8219f17f1b8093b4d02b370c7b008101923b1873
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
