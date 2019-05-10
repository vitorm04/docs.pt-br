---
title: Recomendações do tipo de controle
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- user controls [Windows Forms], when to use
- custom controls [Windows Forms], types
- controls [Windows Forms], creating
ms.assetid: 5235fe9d-c36a-4c08-ae76-6cb90b50085e
ms.openlocfilehash: 9416fc3efabc3fef6b678a3aa3ddef048eed5e2f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648233"
---
# <a name="control-type-recommendations"></a>Recomendações do tipo de controle
O .NET Framework fornece a capacidade de desenvolver e implementar novos controles. Além do controle de usuário familiar, agora você poderá gravar controles personalizados que executam sua os que executam suas próprias pinturas e que podem até mesmo estender as funcionalidades de controles existentes por meio de herança. Decidindo qual tipo de controle criar pode ser confuso. Esta seção destaca as diferenças entre os vários tipos de controles pelos quais você pode herdar e fornece considerações relacionadas ao tipo que você escolher para seu projeto.  
  
> [!NOTE]
>  Caso queira criar um controle para usar no Web Forms, consulte [Desenvolvendo Controles de Servidores ASP.NET Personalizados](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).  
  
## <a name="inheriting-from-a-windows-forms-control"></a>Herdando de um controle dos Windows Forms  
 Você pode derivar um controle herdado de qualquer controle Windows Forms existente. Essa abordagem permite a você reter todas as funcionalidades inerentes de um controle Windows Forms e estender essa funcionalidade adicionando propriedades personalizadas, métodos ou outras funcionalidades. Por exemplo, você pode criar um controle derivado de <xref:System.Windows.Forms.TextBox> que pode aceitar apenas números e converte automaticamente a entrada em um valor. Um controle desse tipo pode conter código de validação que foi chamado sempre que o texto na caixa de texto foi alterado e pode ter uma propriedade adicional, Valor. Em alguns controles, você também pode adicionar uma aparência personalizada para a interface gráfica do seu controle substituindo o <xref:System.Windows.Forms.Control.OnPaint%2A> método da classe base.  
  
 Herde de um controle dos Windows Forms se:  
  
- A maioria da funcionalidade que você precisa já é idêntica a um controle Windows Forms existente.  
  
- Você não precisa de uma interface gráfica personalizada ou deseja criar um novo front-end gráfico para um controle existente.  
  
## <a name="inheriting-from-the-usercontrol-class"></a>Herdando da classe UserControl  
 Um controle de usuário é uma coleção de controles dos Windows Forms encapsulados em um contêiner comum. Um contêiner contém todas as funcionalidades inerentes associadas a cada um dos controles dos Windows Forms e permite que você exponha seletivamente e associe suas propriedades. Um exemplo de um controle composto poderia ser um controle criado para exibir dados de endereço de cliente de um banco de dados. Esse controle incluiria várias caixas de texto para exibir cada campo e controles de botão para navegar pelos registros. Você pode expor seletivamente propriedades de associação de dados, além de poder empacotar e reutilizar todo o controle do aplicativo para o aplicativo.  
  
 Herdar o <xref:System.Windows.Forms.UserControl> classe se:  
  
- Você deseja combinar a funcionalidade de vários controles dos Windows Forms em uma única unidade reutilizável.  
  
## <a name="inheriting-from-the-control-class"></a>Herdando da Classe de Controle  
 Outra maneira de criar um controle é criar um substancialmente novo herdando de <xref:System.Windows.Forms.Control>. O <xref:System.Windows.Forms.Control> classe fornece toda a funcionalidade básica necessária por controles (por exemplo, eventos), mas nenhuma funcionalidade específica do controle ou interface gráfica. Criando um controle herdando a <xref:System.Windows.Forms.Control> classe requer muito mais ponderamento e esforço que herdar de controle de usuário ou um controle Windows Forms existente. O autor deve gravar código para o <xref:System.Windows.Forms.Control.OnPaint%2A> eventos de controle, bem como qualquer código específico do que é necessário. Maior flexibilidade é permitida, no entanto e você pode personalizar um controle para atender às suas necessidades. Um exemplo de um controle personalizado é um controle de relógio que duplica a aparência e a ação de um relógio analógico. A pintura personalizada deve ser invocada para fazer com que os ponteiros do relógio se movam em resposta a <xref:System.Windows.Forms.Timer.Tick> eventos de um componente de temporizador interno.  
  
 Herdar o <xref:System.Windows.Forms.Control> classe se:  
  
- Você deseja fornecer uma representação gráfica personalizada do seu controle.  
  
- Você precisa implementar a funcionalidade personalizada que não está disponível por controles padrão.  
  
- [Como: Exibir um controle na caixa de diálogo de itens de caixa de ferramentas de escolha](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
  
- [Passo a passo: Serializando coleções de tipos padrão com DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)  
  
- [Passo a passo: Herdando um controle de formulários do Windows com VisualC#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
  
- [Como: Fornecer um Bitmap da caixa de ferramentas para um controle](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
  
- [Como: Herdar controles de formulários do Windows existentes](how-to-inherit-from-existing-windows-forms-controls.md)  
  
- [Passo a passo: Depuração de controles personalizados do Windows Forms em tempo de design](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
  
- [Como: Herdar da classe de controle](how-to-inherit-from-the-control-class.md)  
  
- [Como: Testar o comportamento de tempo de execução de um UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
  
- [Como: Alinhar um controle às bordas de formulários no tempo de Design](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
  
- [Como: Herdar da classe UserControl](how-to-inherit-from-the-usercontrol-class.md)  
  
- [Como: Criar controles para Windows Forms](how-to-author-controls-for-windows-forms.md)  
  
- [Como: Criar controles compostos](how-to-author-composite-controls.md)  
  
- [Passo a passo: Criando um controle composto com o Visual Basic](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
  
- [Passo a passo: Criando um controle composto com VisualC#](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
  
- [Passo a passo: Herdando um controle de formulários do Windows com o Visual Basic](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
  
- [Passo a passo: Criando um controle de formulários do Windows que tira proveito dos recursos de tempo de Design do Visual Studio](creating-a-wf-control-design-time-features.md)  
  
- [Como: Criar um controle de formulários do Windows que tira proveito dos recursos de tempo de Design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))  
  
## <a name="see-also"></a>Consulte também

- [Como: Desenvolver um controle de formulários do Windows simples](how-to-develop-a-simple-windows-forms-control.md)
- [Variedades de controles personalizados](varieties-of-custom-controls.md)
