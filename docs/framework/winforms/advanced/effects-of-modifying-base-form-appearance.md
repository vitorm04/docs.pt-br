---
title: Efeitos da modificação da aparência de um formulário base
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms [Windows Forms]
- inherited forms [Windows Forms], modifications to base form
- Windows Forms, base form appearance
- base forms
- inheritance [Windows Forms], forms
ms.assetid: 1c3f2b29-a05c-4c6f-aa1a-4e66b94f343a
ms.openlocfilehash: 5239017eb63ca6360ae8811a76497256fafbd1b1
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040142"
---
# <a name="effects-of-modifying-a-base-forms-appearance"></a>Efeitos da modificação da aparência de um formulário base

Durante o desenvolvimento de aplicativos, você geralmente precisa alterar a aparência do formulário base do qual outros formulários no projeto (ou em outros projetos) estão herdando.

No momento do design, as alterações na aparência do formulário base (seja a configuração das propriedades ou a adição e a subtração de controles) são refletidas nos formulários herdados quando o projeto que contém o formulário base é criado. Não é suficiente para você simplesmente salvar as alterações no formulário base. Para criar um projeto, escolha **Compilar** no menu **Compilar** .

As modificações feitas no formulário base em tempo de execução não afetam os formulários herdados já instanciados.

## <a name="see-also"></a>Consulte também

- [base](~/docs/csharp/language-reference/keywords/base.md)
- [Como: Herdar Windows Forms](how-to-inherit-windows-forms.md)
- [Herança Visual dos Windows Forms](windows-forms-visual-inheritance.md)
