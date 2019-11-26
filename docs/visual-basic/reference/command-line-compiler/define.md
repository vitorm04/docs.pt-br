---
title: -define
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: fd0875f09bf3ba7211ede500aa0da45f8b7cd2c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344772"
---
# <a name="-define-visual-basic"></a>-define (Visual Basic)
Define as constantes de compilador condicional.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-define:["]symbol[=value][,symbol[=value]]["]  
```

ou

```console  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`symbol`|Necessário. O símbolo a ser definido.|  
|`value`|Opcional. O valor para atribuir `symbol`. If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks. Se nenhum valor for especificado, será considerado como True.|  
  
## <a name="remarks"></a>Comentários  
 The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.  
  
 Você pode usar símbolos criados por essa opção com a diretiva `#If`...`Then`...`#Else` para compilar os arquivos de origem condicionalmente.  
  
 `-d` é a forma abreviada de `-define`.  
  
 Você pode definir vários símbolos com `-define` usando uma vírgula para separar as definições de símbolos.  
  
|Para configurar /define no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Have a project selected in **Solution Explorer**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Click the **Compile** tab.<br />3.  Click **Advanced**.<br />4.  Modify the value in the **Custom Constants** box.|  
  
## <a name="example"></a>Exemplo  
 O código a seguir define e usa duas constantes de compilador condicional.  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Diretivas #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Diretiva #Const](../../../visual-basic/language-reference/directives/const-directive.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
