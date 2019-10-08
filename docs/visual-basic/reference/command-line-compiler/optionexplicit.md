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
ms.openlocfilehash: 5c0946b94bfe02d797d1a484088869375703eb6a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005309"
---
# <a name="-optionexplicit"></a>-optionexplicit
Faz com que o compilador Relate erros se as variáveis não forem declaradas antes de serem usadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Argumentos  
 `+` &#124; `-`  
 Opcional. Especifique `-optionexplicit+` para exigir declaração explícita de variáveis. A opção `-optionexplicit+` é o padrão e é a mesma que `-optionexplicit`. A opção `-optionexplicit-` habilita a declaração implícita de variáveis.  
  
## <a name="remarks"></a>Comentários  
 Se o arquivo de código-fonte contiver uma [instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md), a instrução substituirá a configuração do compilador de linha de comando `-optionexplicit`.  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>Para Set-optionexplicit no IDE do Visual Studio  
  
1. Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**.   
  
2. Clique na guia **Compilar**.  
  
3. Modifique o valor na caixa **Option Explicit** .  
  
## <a name="example"></a>Exemplo  
 O código a seguir é compilado quando `-optionexplicit-` é usado.  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
