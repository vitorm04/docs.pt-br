---
title: Como herdar Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
ms.openlocfilehash: 275ae52a36ed9766e2569bd6c8ecdea78ea56e0b
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44507744"
---
# <a name="how-to-inherit-windows-forms"></a>Como herdar Windows Forms
Criar novo Windows Forms herdando de formulários base é uma maneira prática de duplicar seus melhores esforços sem passar pelo processo de recriar inteiramente um formulário toda vez que precisar dele.  
  
 Para mais informações sobre herdar formulários em tempo de design usando a caixa de diálogo **Selecionador de Herança** e como distinguir visualmente entre níveis de segurança de controles herdados, consulte [Como herdar formulários usando a caixa de diálogo selecionador de herança](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).  
  
 **Observação** para herdar de um formulário, o arquivo ou namespace que contém esse formulário deve ter sido incorporado em um arquivo executável ou DLL. Para compilar o projeto, escolha **Compilar** no menu **Compilar**. Além disso, uma referência ao namespace deve ser adicionada à classe que herda o formulário. As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-inherit-a-form-programmatically"></a>Herdar um formulário programaticamente  
  
1.  Em sua classe, adicione uma referência ao namespace que contém o formulário que se deseja herdar.  
  
2.  Na definição de classe, adicione uma referência ao formulário de onde será herdado. A referência deve incluir o namespace que contém o formulário seguido por uma vírgula, depois o nome do próprio formulário base.  
  
    ```vb  
    Public Class Form2  
        Inherits Namespace1.Form1  
    ```  
  
    ```csharp  
    public class Form2 : Namespace1.Form1  
    ```  
  
 Ao herdar formulários, tenha em mente que podem surgir problemas em relação a manipuladores de eventos sendo chamado duas vezes, porque cada evento está sendo manipulado pela classe base e pela classe herdada. para mais informações sobre como evitar esse problema, consulte [Solucionando problemas de manipuladores de eventos herdados no Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Inherits](~/docs/visual-basic/language-reference/statements/inherits-statement.md)  
 [Instrução Imports (Tipo e Namespace .NET)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [using](~/docs/csharp/language-reference/keywords/using.md)  
 [Efeitos da Modificação da Aparência de um Formulário Base](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 [Herança Visual dos Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
