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
ms.openlocfilehash: 267a56cbfd9025e2e20f1468535e5544146535a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="developing-windows-forms-controls-at-design-time"></a>Desenvolvendo controles dos Windows Forms na hora de design
Para autores de controle, o .NET Framework fornece uma ampla variedade de tecnologia de criação de controle. Os autores não estão mais limitados a criar controles de composição que atuam como uma coleção de controles preexistentes. Por meio de herança, você pode criar seus próprios controles de com base em controles de composição preexistentes ou controles dos Windows Forms preexistentes. Você também pode criar seus próprios controles que implementam pintura personalizada. Essas opções possibilitam muita flexibilidade no design e a funcionalidade da interface visual. Para aproveitar esses recursos, familiarize-se com os conceitos de programação baseada em objeto.  
  
> [!NOTE]
>  Não é necessário ter uma compreensão completa de herança, mas talvez seja útil para se referir a [Noções básicas de herança (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Caso queira criar controles personalizados para usar em Web Forms, consulte [Desenvolvendo Controles Personalizados ASP.NET Server](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Passo a passo: criando um controle de composição com o Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 Mostra como criar um controle de composição simples em Visual Basic.  
  
 [Passo a passo: criando um controle de composição com o Visual C#](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 Mostra como criar um controle de composição simples em C#.  
  
 [Passo a passo: herdando um controle dos Windows Forms com Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 Mostra como criar um controle simples dos Windows Forms usando herança no Visual Basic.  
  
 [Passo a passo: herdando um controle dos Windows Forms com Visual C#](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 Mostra como criar um controle simples dos Windows Forms usando herança em C#.  
  
 [Passo a passo: realizando tarefas comuns usando smart tags em controles dos Windows Forms](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 Mostra como usar o recurso de smart tag em controles dos Windows Forms.  
  
 [Passo a passo: serializando coleções de tipos padrão com DesignerSerializationVisibilityAttribute](../../../../docs/framework/winforms/controls/serializing-collections-designerserializationvisibilityattribute.md)  
 Mostra como usar o <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> atributo para serializar uma coleção.  
  
 [Passo a passo: depurando controles personalizados dos Windows Forms em tempo de Design](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 Mostra como depurar o comportamento de tempo de design de um controle dos Windows Forms.  
  
 [Passo a passo: criando um controle dos Windows Forms que aproveita os recursos de tempo de design do Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 Mostra como integrar fortemente um controle de composição ao ambiente de design.  
  
 [Como Criar Controles para o Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 Apresenta uma visão geral de considerações para implementar um controle dos Windows Forms.  
  
 [Como criar controles de composição](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 Mostra como criar um controle herdando de um controle de composição.  
  
 [Como herdar da classe UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 Fornece uma visão geral do procedimento para criar um controle de composição.  
  
 [Como herdar de controles dos Windows Forms existentes](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 Mostra como criar um controle estendido, herdando a <xref:System.Windows.Forms.Button> classe de controle.  
  
 [Como herdar da classe de controle](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 Apresenta uma visão geral da criação de um controle estendido.  
  
 [Como alinhar um controle às bordas de formulários no tempo de design](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 Mostra como usar o <xref:System.Windows.Forms.Control.Dock%2A> propriedade para alinhar o controle para a borda da forma que ele ocupe.  
  
 [Como exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 Mostra o procedimento para instalar seu controle de modo que ele apareça na caixa de diálogo **Personalizar caixa de ferramentas**.  
  
 [Como fornecer um bitmap da caixa de ferramentas para um controle](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 Mostra como usar o <xref:System.Drawing.ToolboxBitmapAttribute> para exibir um ícone ao lado de seu controle personalizado no **caixa de ferramentas**.  
  
 [Como testar o comportamento de tempo de execução de um UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 Mostra como usar o **Contêiner de Teste UserControl** para testar o comportamento de um controle de composição.  
  
 [Erros de tempo de design no Designer de Formulários do Windows](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 Explica o significado e o uso da lista de erros de tempo de design que aparece no Microsoft Visual Studio quando o carregamento do Designer de Formulários do Windows falha.  
  
 [Solução de problemas de criação de controle e de componente](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 Mostra como diagnosticar e corrigir problemas comuns que podem ocorrer quando você criar um controle ou componente personalizado.  
  
## <a name="reference"></a>Referência  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 Descreve essa classe e tem links para todos os seus membros.  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 Descreve essa classe e tem links para todos os seus membros.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 Discute como criar seus próprios controles personalizados com o .NET Framework.  
  
 [Componentes de independência de linguagem e componentes independentes da linguagem](../../../../docs/standard/language-independence-and-language-independent-components.md)  
 Apresenta o Common Language Runtime, que foi projetado para simplificar a criação e uso de componentes. Um aspecto importante dessa simplificação é melhor interoperabilidade entre componentes escritos usando diferentes linguagens de programação. A CLS (Common Language Specification) possibilita criar ferramentas e componentes que funcionam com várias linguagens de programação.  
  
 [Passo a passo: preenchendo automaticamente a caixa de ferramentas com componentes personalizados](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 Descreve como habilitar seu componente ou controle para ser exibido na caixa de diálogo **Personalizar Caixa de Ferramentas**.
