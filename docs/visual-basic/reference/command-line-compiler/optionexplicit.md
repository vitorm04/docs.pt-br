---
title: -optionexplicit
ms.date: 07/20/2015
f1_keywords:
- /optionexplicit
- -optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
ms.openlocfilehash: 54d438541e8840e4394b24b20b4f394ff8cdb820
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59332385"
---
# <a name="-optionexplicit"></a>-optionexplicit
Faz com que o compilador relatar erros se variáveis não forem declaradas antes de serem usadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Opcional. Especifique `-optionexplicit+` para exigir a declaração explícita de variáveis. O `-optionexplicit+` opção é o padrão e é o mesmo que `-optionexplicit`. O `-optionexplicit-` opção permite que a declaração implícita de variáveis.  
  
## <a name="remarks"></a>Comentários  
 Se o arquivo de código fonte contém um [instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md), a instrução substitui a `-optionexplicit` configuração do compilador de linha de comando.  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>Definir - optionexplicit no IDE do Visual Studio  
  
1. Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**.   
  
2. Clique na guia **Compilar**.  
  
3. Modificar o valor de **Option Explicit** caixa.  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila quando `-optionexplicit-` é usado.  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
