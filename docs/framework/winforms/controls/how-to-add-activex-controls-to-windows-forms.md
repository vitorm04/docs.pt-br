---
title: Como adicionar controles ActiveX aos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: c851a215638e60642bf93564f4884b5a79d430d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a>Como adicionar controles ActiveX aos Windows Forms
Enquanto o Designer de Formulários do Windows é otimizado para hospedar controles dos Windows Forms, também é possível colocar controles ActiveX nos Windows Forms.  
  
> [!CAUTION]
>  Há limitações de desempenho para o Windows Forms quando os controles ActiveX são adicionados a ele.  
  
 Antes de adicionar controles ActiveX ao seu formulário, você deve adicioná-los à caixa de ferramentas. Para obter mais informações, consulte [Componentes COM, Caixa de diálogo Personalizar caixa de ferramentas](http://msdn.microsoft.com/library/171333f3-f207-4e02-bbdc-17862556212c).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, clique em **Importar e exportar configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a>Para adicionar um controle ActiveX ao seu Windows Form  
  
-   Clique duas vezes no controle na Caixa de ferramentas.  
  
     O Visual Studio adiciona todas as referências para o controle em seu projeto. Para obter mais informações sobre as coisas para ter em mente ao usar controles ActiveX nos Windows Forms, consulte [Considerações sobre quando hospedar um controle ActiveX em um Windows Form](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md).  
  
    > [!NOTE]
    >  O Importador de controle ActiveX dos Windows Forms (AxImp.exe) cria os argumentos de evento de um tipo diferente do que o esperado após a importação de bibliotecas de link dinâmico do ActiveX. Os argumentos criados pelo AxImp.exe são semelhantes ao seguinte: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, quando `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` for esperado. Lembre-se de que essa irregularidade não impede que o código funcione normalmente. Para obter detalhes, consulte [Importador de Controle ActiveX dos Windows Forms (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md).  
  
## <a name="see-also"></a>Consulte também  
 [Controles dos Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Controles e objetos programáveis comparados em diversas linguagens e bibliotecas](http://msdn.microsoft.com/library/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [Como Adicionar Controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [Organizando Controles nos Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Controles dos Windows Forms por função](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
