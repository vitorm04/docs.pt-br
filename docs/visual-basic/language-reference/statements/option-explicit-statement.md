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
ms.openlocfilehash: 19ff8cf1dbcdb941e38f23be4cb68d3a5e5b83a8
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582576"
---
# <a name="option-explicit-statement-visual-basic"></a>Instrução Option Explicit (Visual Basic)
Força a declaração explícita de todas as variáveis em um arquivo ou permite declarações implícitas de variáveis.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a>Partes  
 `On`  
 Opcional. Habilita a verificação de `Option Explicit`. Se `On` ou `Off` não for especificado, o padrão será `On`.  
  
 `Off`  
 Opcional. Desabilita a verificação de `Option Explicit`.  
  
## <a name="remarks"></a>Comentários  
 Quando `Option Explicit On` ou `Option Explicit` aparece em um arquivo, você deve declarar explicitamente todas as variáveis usando as instruções `Dim` ou `ReDim`. Se você tentar usar um nome de variável não declarado, ocorrerá um erro no momento da compilação. A instrução `Option Explicit Off` permite a declaração implícita de variáveis.  
  
 Se usado, a instrução `Option Explicit` deve aparecer em um arquivo antes de quaisquer outras instruções de código-fonte.  
  
> [!NOTE]
> A definição de `Option Explicit` para `Off` geralmente não é uma boa prática. Você poderia digitar incorretamente um nome de variável em um ou mais locais, o que levaria a resultados inesperados na execução do programa.  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a>Quando uma instrução Option Explicit não está presente  
 Se o código-fonte não contiver uma instrução `Option Explicit`, a opção de configuração **explícita** na [página compilar, designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) será usada. Se o compilador de linha de comando for usado, a opção de compilador [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) será usada.  
  
#### <a name="to-set-option-explicit-in-the-ide"></a>Para definir a opção Explicit no IDE  
  
1. No **Gerenciador de Soluções**, selecione um projeto. No menu **Projeto**, clique em **Propriedades**.  
  
2. Clique na guia **Compilar**.  
  
3. Defina o valor na caixa **Option Explicit** .  
  
 Quando você cria um novo projeto, a **opção configuração explícita** na guia **Compilar** é definida como a **opção configuração explícita** na caixa de diálogo **padrões do VB** . Para acessar a caixa de diálogo **padrões do VB** , no menu **ferramentas** , clique em **Opções**. Na caixa de diálogo **Opções**, expanda **Projetos e Soluções** e, em seguida, clique em **Padrões de VB**. A configuração padrão inicial em **padrões do VB** é `On`.  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a>Para definir a opção Explicit na linha de comando  
  
- Inclua a opção de compilador [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) no comando **Vbc** .  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a instrução `Option Explicit` para forçar a declaração explícita de todas as variáveis. A tentativa de usar uma variável não declarada causa um erro no tempo de compilação.  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a>Consulte também

- [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
