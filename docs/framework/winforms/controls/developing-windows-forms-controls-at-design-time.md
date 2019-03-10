---
title: Desenvolvendo controles dos Windows Forms na hora de design
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls [Windows Forms]
- Windows Forms controls, creating
- controls [Windows Forms]
- controls [Windows Forms], creating
- user controls [Windows Forms]
- custom controls [Windows Forms]
ms.assetid: e5a8e088-7ec8-4fd9-bcb3-9078fd134829
ms.openlocfilehash: 641a6c1c99169c6836c33b3e84b2ae02aba298d2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707710"
---
# <a name="developing-windows-forms-controls-at-design-time"></a>Desenvolvendo controles dos Windows Forms na hora de design
Para autores de controle, o .NET Framework fornece uma ampla variedade de tecnologia de criação de controle. Os autores não estão mais limitados a criar controles de composição que atuam como uma coleção de controles preexistentes. Por meio de herança, você pode criar seus próprios controles de com base em controles de composição preexistentes ou controles dos Windows Forms preexistentes. Você também pode criar seus próprios controles que implementam pintura personalizada. Essas opções possibilitam muita flexibilidade no design e a funcionalidade da interface visual. Para aproveitar esses recursos, familiarize-se com os conceitos de programação baseada em objeto.  
  
> [!NOTE]
>  Não é necessário ter uma compreensão completa de herança, mas talvez você ache útil consultar [Noções básicas de herança (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Caso queira criar controles personalizados para usar em Web Forms, consulte [Desenvolvendo Controles Personalizados ASP.NET Server](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Passo a passo: Criando um controle composto com o Visual Basic](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 Mostra como criar um controle de composição simples em Visual Basic.  
  
 [Passo a passo: Criando um controle composto com VisualC#](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 Mostra como criar um controle de composição simples em C#.  
  
 [Passo a passo: Herdando um controle de formulários do Windows com o Visual Basic](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 Mostra como criar um controle simples dos Windows Forms usando herança no Visual Basic.  
  
 [Passo a passo: Herdando um controle de formulários do Windows com VisualC#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 Mostra como criar um controle simples dos Windows Forms usando herança em C#.  
  
 [Passo a passo: Realizando tarefas comuns usando Smart Tags no Windows, controles de formulários](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 Mostra como usar o recurso de smart tag em controles dos Windows Forms.  
  
 [Passo a passo: Serializando coleções de tipos padrão com DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)  
 Mostra como usar o <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> atributo para serializar uma coleção.  
  
 [Passo a passo: Depuração de controles personalizados do Windows Forms em tempo de design](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 Mostra como depurar o comportamento de tempo de design de um controle dos Windows Forms.  
  
 [Passo a passo: Criando um controle de formulários do Windows que tira proveito dos recursos de tempo de Design do Visual Studio](creating-a-wf-control-design-time-features.md)  
 Mostra como integrar fortemente um controle de composição ao ambiente de design.  
  
 [Como: Criar controles para Windows Forms](how-to-author-controls-for-windows-forms.md)  
 Apresenta uma visão geral de considerações para implementar um controle dos Windows Forms.  
  
 [Como: Criar controles compostos](how-to-author-composite-controls.md)  
 Mostra como criar um controle herdando de um controle de composição.  
  
 [Como: Herdar da classe UserControl](how-to-inherit-from-the-usercontrol-class.md)  
 Fornece uma visão geral do procedimento para criar um controle de composição.  
  
 [Como: Herdar controles de formulários do Windows existentes](how-to-inherit-from-existing-windows-forms-controls.md)  
 Mostra como criar um controle estendido herdando a <xref:System.Windows.Forms.Button> classe de controle.  
  
 [Como: Herdar da classe de controle](how-to-inherit-from-the-control-class.md)  
 Apresenta uma visão geral da criação de um controle estendido.  
  
 [Como: Alinhar um controle às bordas de formulários no tempo de Design](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 Mostra como usar o <xref:System.Windows.Forms.Control.Dock%2A> propriedade para alinhar o controle na borda da forma que ele ocupa.  
  
 [Como: Exibir um controle na caixa de diálogo de itens de caixa de ferramentas de escolha](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 Mostra o procedimento para instalar seu controle de modo que ele apareça na caixa de diálogo **Personalizar caixa de ferramentas**.  
  
 [Como: Fornecer um Bitmap da caixa de ferramentas para um controle](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 Mostra como usar o <xref:System.Drawing.ToolboxBitmapAttribute> para exibir um ícone ao lado de seu controle personalizado na **caixa de ferramentas**.  
  
 [Como: Testar o comportamento de tempo de execução de um UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 Mostra como usar o **Contêiner de Teste UserControl** para testar o comportamento de um controle de composição.  
  
 [Erros de tempo de design no Designer de Formulários do Windows](design-time-errors-in-the-windows-forms-designer.md)  
 Explica o significado e o uso da lista de erros de tempo de design que aparece no Microsoft Visual Studio quando o carregamento do Designer de Formulários do Windows falha.  
  
 [Solução de problemas de criação de controle e de componente](troubleshooting-control-and-component-authoring.md)  
 Mostra como diagnosticar e corrigir problemas comuns que podem ocorrer quando você criar um controle ou componente personalizado.  
  
## <a name="reference"></a>Referência  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 Descreve essa classe e tem links para todos os seus membros.  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 Descreve essa classe e tem links para todos os seus membros.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework](developing-custom-windows-forms-controls.md)  
 Discute como criar seus próprios controles personalizados com o .NET Framework.  
  
 [Componentes de independência de linguagem e componentes independentes da linguagem](../../../standard/language-independence-and-language-independent-components.md)  
 Apresenta o Common Language Runtime, que foi projetado para simplificar a criação e uso de componentes. Um aspecto importante dessa simplificação é melhor interoperabilidade entre componentes escritos usando diferentes linguagens de programação. A CLS (Common Language Specification) possibilita criar ferramentas e componentes que funcionam com várias linguagens de programação.  
  
 [Passo a passo: Preenchendo automaticamente a caixa de ferramentas com componentes personalizados](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 Descreve como habilitar seu componente ou controle para ser exibido na caixa de diálogo **Personalizar Caixa de Ferramentas**.
