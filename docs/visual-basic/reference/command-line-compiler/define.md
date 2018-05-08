---
title: -Definir (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4de37c58543aed9ed13be8b0d2bcec9830ca9082
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="-define-visual-basic"></a>-Definir (Visual Basic)
Define as constantes de compilador condicional.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`symbol`|Obrigatório. O símbolo a ser definido.|  
|`value`|Opcional. O valor para atribuir `symbol`. Se `value` é uma cadeia de caracteres, ele deve estar entre sequências de barra invertida/aspas (\\") em vez de aspas. Se nenhum valor for especificado, será considerado como True.|  
  
## <a name="remarks"></a>Comentários  
 O `-define` opção tem um efeito semelhante ao uso de um `#Const` no arquivo de origem, exceto que constantes definidas pela diretiva de pré-processador `-define` são públicos e se aplicam a todos os arquivos no projeto.  
  
 Você pode usar símbolos criados por essa opção com a diretiva `#If`...`Then`...`#Else` para compilar os arquivos de origem condicionalmente.  
  
 `-d` é a forma abreviada de `-define`.  
  
 Você pode definir vários símbolos com `-define` usando uma vírgula para separar as definições de símbolos.  
  
|Para configurar /define no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Compilar**.<br />3.  Clique em **Avançadas**.<br />4.  Modificar o valor de **constantes personalizadas** caixa.|  
  
## <a name="example"></a>Exemplo  
 O código a seguir define e usa duas constantes de compilador condicional.  
  
 [!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Diretivas #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Diretiva #Const](../../../visual-basic/language-reference/directives/const-directive.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
