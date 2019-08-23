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
ms.openlocfilehash: b24bd2db564c7acb0a748c47095ee0777ea1eb88
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955156"
---
# <a name="effects-of-modifying-a-base-forms-appearance"></a>Efeitos da modificação da aparência de um formulário base

Durante o desenvolvimento de aplicativos, você geralmente precisa alterar a aparência do formulário base do qual outros formulários no projeto (ou em outros projetos) estão herdando.

No momento do design, as alterações na aparência do formulário base (seja a configuração das propriedades ou a adição e a subtração de controles) são refletidas nos formulários herdados quando o projeto que contém o formulário base é criado. Não é suficiente para você simplesmente salvar as alterações no formulário base. Para criar um projeto, escolha **Compilar** no menu **Compilar** .

As modificações feitas no formulário base em tempo de execução não afetam os formulários herdados já instanciados.

## <a name="see-also"></a>Consulte também

- [base](../../../csharp/language-reference/keywords/base.md)
- [Como: Herdar Windows Forms](how-to-inherit-windows-forms.md)
- [Herança Visual dos Windows Forms](windows-forms-visual-inheritance.md)
