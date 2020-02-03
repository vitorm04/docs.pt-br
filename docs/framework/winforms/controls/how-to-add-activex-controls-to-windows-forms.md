---
title: Adicionar controles ActiveX a formulários
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 920c1111a5703352a4b624068e3d5ceae9892591
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746848"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a>Como adicionar controles ActiveX aos Windows Forms

Embora o Designer de Formulários do Windows no Visual Studio seja otimizado para hospedar controles de Windows Forms, você também pode colocar controles ActiveX em Windows Forms.

> [!CAUTION]
> Há limitações de desempenho para o Windows Forms quando os controles ActiveX são adicionados a ele.

Antes de adicionar controles ActiveX ao seu formulário, você deve adicioná-los à caixa de ferramentas. Para obter mais informações, consulte [Componentes COM, Caixa de diálogo Personalizar caixa de ferramentas](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).

## <a name="add-an-activex-control-to-your-windows-form"></a>Adicionar um controle ActiveX ao seu formulário do Windows

Para adicionar um controle ActiveX ao seu formulário do Windows, clique duas vezes no controle na caixa de ferramentas.

O Visual Studio adiciona todas as referências ao controle em seu projeto. Para obter mais informações sobre as coisas para ter em mente ao usar controles ActiveX nos Windows Forms, consulte [Considerações sobre quando hospedar um controle ActiveX em um Windows Form](considerations-when-hosting-an-activex-control-on-a-windows-form.md).

> [!NOTE]
> O Importador de controle ActiveX dos Windows Forms (AxImp.exe) cria os argumentos de evento de um tipo diferente do que o esperado após a importação de bibliotecas de link dinâmico do ActiveX. Os argumentos criados pelo AxImp.exe são semelhantes ao seguinte: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, quando `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` for esperado. Lembre-se de que essa irregularidade não impede que o código funcione normalmente. Para obter detalhes, consulte [Importador de Controle ActiveX dos Windows Forms (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).

## <a name="see-also"></a>Consulte também

- [Controles dos Windows Forms](index.md)
- [Controles e objetos programáveis comparados em diversas linguagens e bibliotecas](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [Como Adicionar Controles ao Windows Forms](how-to-add-controls-to-windows-forms.md)
- [Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Controles a serem usados no Windows Forms](controls-to-use-on-windows-forms.md)
- [Controles dos Windows Forms por função](windows-forms-controls-by-function.md)
