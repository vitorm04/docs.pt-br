---
title: Herança de formulário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
ms.openlocfilehash: cc3a4cc75fd13e8f193a6920ed5b4a9bc8fd5d74
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743326"
---
# <a name="how-to-inherit-windows-forms"></a>Como herdar Windows Forms

Criar novo Windows Forms herdando de formulários base é uma maneira prática de duplicar seus melhores esforços sem passar pelo processo de recriar inteiramente um formulário toda vez que precisar dele.

Para mais informações sobre herdar formulários em tempo de design usando a caixa de diálogo **Selecionador de Herança** e como distinguir visualmente entre níveis de segurança de controles herdados, consulte [Como herdar formulários usando a caixa de diálogo selecionador de herança](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).

> [!NOTE]
> Para herdar de um formulário, o arquivo ou namespace que contém esse formulário deve ter sido compilado em um arquivo executável ou DLL. Para compilar o projeto, escolha **Compilar** no menu **Compilar**. Além disso, uma referência ao namespace deve ser adicionada à classe que herda o formulário.

## <a name="inherit-a-form-programmatically"></a>Herdar um formulário programaticamente

1. Em sua classe, adicione uma referência ao namespace que contém o formulário que se deseja herdar.

2. Na definição de classe, adicione uma referência ao formulário de onde será herdado. A referência deve incluir o namespace que contém o formulário seguido por uma vírgula, depois o nome do próprio formulário base.

    ```vb
    Public Class Form2
        Inherits Namespace1.Form1
    ```

    ```csharp
    public class Form2 : Namespace1.Form1
    ```

 Ao herdar formulários, tenha em mente que podem surgir problemas em relação a manipuladores de eventos sendo chamado duas vezes, porque cada evento está sendo manipulado pela classe base e pela classe herdada. para mais informações sobre como evitar esse problema, consulte [Solucionando problemas de manipuladores de eventos herdados no Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).

## <a name="see-also"></a>Veja também

- [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Instrução Imports (Tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [using](../../../csharp/language-reference/keywords/using.md)
- [Efeitos da Modificação da Aparência de um Formulário Base](effects-of-modifying-base-form-appearance.md)
- [Herança visual do Windows Forms](windows-forms-visual-inheritance.md)
