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
# <a name="directives-visual-basic"></a>Diretivas (Visual Basic)

Os tópicos nesta seção documentam as diretivas Visual Basic do compilador do código-fonte.  
  
## <a name="in-this-section"></a>Nesta seção  

 [Diretiva #Const](../../../visual-basic/language-reference/directives/const-directive.md) – definir uma constante do compilador  
  
 [Diretiva #ExternalSource](../../../visual-basic/language-reference/directives/externalsource-directive.md) --indica um mapeamento entre linhas de origem e texto externo à origem  
  
 [#If... Then... #Else diretivas](../../../visual-basic/language-reference/directives/if-then-else-directives.md) – compilar blocos de código selecionados  
  
 [Diretiva #Region](../../../visual-basic/language-reference/directives/region-directive.md) – recolher e ocultar seções de código no editor do Visual Studio  
  
 **#Disable, #Enable** --desabilitar e habilitar avisos específicos para regiões de código.  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 Você também pode desabilitar e habilitar uma lista separada por vírgulas de códigos de aviso.  
  
## <a name="related-sections"></a>Seções relacionadas  

 [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md)  
  
 [Visual Basic](../../../visual-basic/index.md)
