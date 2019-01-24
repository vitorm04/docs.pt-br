---
title: Instrução Option Explicit (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
helpviewer_keywords:
- declaring variables [Visual Basic], explicit
- forced variable declaration in Option Explicit statement [Visual Basic]
- Explicit keyword
- explicit variable declaration
- Option Explicit statement [Visual Basic]
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
ms.openlocfilehash: a52900f36ee20e827518598a97c7b7f867bd0d43
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586820"
---
# <a name="option-explicit-statement-visual-basic"></a>Instrução Option Explicit (Visual Basic)
Força a declaração explícita de todas as variáveis em um arquivo ou permite que as declarações implícitas de variáveis.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a>Partes  
 `On`  
 Opcional. Habilita `Option Explicit` verificando. Se `On` ou `Off` não for especificado, o padrão é `On`.  
  
 `Off`  
 Opcional. Desabilita `Option Explicit` verificando.  
  
## <a name="remarks"></a>Comentários  
 Quando `Option Explicit On` ou `Option Explicit` aparece em um arquivo, você deve declarar explicitamente todas as variáveis usando o `Dim` ou `ReDim` instruções. Se você tentar usar um nome de variável não declarado, ocorrerá um erro em tempo de compilação. O `Option Explicit Off` instrução permite que a declaração implícita de variáveis.  
  
 Se usado, a instrução `Option Explicit` deve aparecer em um arquivo antes de quaisquer outras instruções de código-fonte.  
  
> [!NOTE]
>  Definindo `Option Explicit` para `Off` geralmente não é uma boa prática. Você poderia digitar incorretamente um nome de variável em um ou mais locais, o que levaria a resultados inesperados na execução do programa.  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a>Quando uma instrução Option Explicit não está presente  
 Se o código-fonte não contiver uma `Option Explicit` instrução, o **Option Explicit** definindo no [página de compilação, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) é usado. Se o compilador de linha de comando é usado, o [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) opção de compilador é usada.  
  
#### <a name="to-set-option-explicit-in-the-ide"></a>Para definir o Option Explicit no IDE  
  
1.  No **Gerenciador de Soluções**, selecione um projeto. No menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique na guia **Compilar**.  
  
3.  Defina o valor na **Option Explicit** caixa.  
  
 Quando você cria um novo projeto, o **Option Explicit** definindo na **compilar** for definido como o **Option Explicit** definindo no **padrões de VB**caixa de diálogo. Para acessar o **padrões de VB** caixa de diálogo do **ferramentas** menu, clique em **opções**. Na caixa de diálogo **Opções**, expanda **Projetos e Soluções** e, em seguida, clique em **Padrões de VB**. A configuração inicial padrão nos **padrões de VB** é `On`.  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a>Para definir o Option Explicit na linha de comando  
  
-   Incluir o [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) opção de compilador na **vbc** comando.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Option Explicit` instrução para forçar a declaração explícita de todas as variáveis. Tentativa de usar uma variável não declarada causa um erro em tempo de compilação.  
  
 [!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]  
  
 [!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]  
  
## <a name="see-also"></a>Consulte também
- [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
