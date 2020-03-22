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
ms.openlocfilehash: 37ccd14dae0ebba2535185f2646e312d9bb70390
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266723"
---
# <a name="-optionexplicit"></a>-optionexplicit
Faz com que o compilador reporte erros se as variáveis não forem declaradas antes de serem usadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Argumentos  
 `+` &#124; `-`  
 Opcional. Especificar `-optionexplicit+` para exigir declaração explícita de variáveis. A `-optionexplicit+` opção é o padrão `-optionexplicit`e é a mesma que . A `-optionexplicit-` opção permite a declaração implícita das variáveis.  
  
## <a name="remarks"></a>Comentários  
 Se o arquivo de código-fonte contiver uma `-optionexplicit` [instrução Option Explicit,](../../../visual-basic/language-reference/statements/option-explicit-statement.md)a instrução substitui a configuração do compilador de linha de comando.  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>Para definir -opçãoexplícita no Visual Studio IDE  
  
1. Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto** , clique em **Propriedades**.
  
2. Clique na guia **Compilar**.  
  
3. Modifique o valor na **caixa Opção Explícita.**  
  
## <a name="example"></a>Exemplo  
 O código a seguir `-optionexplicit-` compila quando é usado.  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a>Confira também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-opçãocomparar](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
