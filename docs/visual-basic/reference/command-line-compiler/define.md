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
ms.openlocfilehash: d0a483e7a3c9e9863db39e89d655cf172c1e8c81
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834303"
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
|`symbol`|Necessário. O símbolo a ser definido.|  
|`value`|Opcional. O valor para atribuir `symbol`. Se `value` é uma cadeia de caracteres, ele deverá ser colocado entre sequências de barra invertida/aspas (\\") em vez de aspas. Se nenhum valor for especificado, será considerado como True.|  
  
## <a name="remarks"></a>Comentários  
 O `-define` opção tem um efeito semelhante ao uso de um `#Const` diretiva de pré-processador em seu arquivo de origem, exceto que as constantes definidas com `-define` são públicos e se aplicam a todos os arquivos no projeto.  
  
 Você pode usar símbolos criados por essa opção com a diretiva `#If`...`Then`...`#Else` para compilar os arquivos de origem condicionalmente.  
  
 `-d` é a forma abreviada de `-define`.  
  
 Você pode definir vários símbolos com `-define` usando uma vírgula para separar as definições de símbolos.  
  
|Para configurar /define no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Compilar**.<br />3.  Clique em **Avançadas**.<br />4.  Modificar o valor de **constantes personalizadas** caixa.|  
  
## <a name="example"></a>Exemplo  
 O código a seguir define e usa duas constantes de compilador condicional.  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Diretivas #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Diretiva #Const](../../../visual-basic/language-reference/directives/const-directive.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
