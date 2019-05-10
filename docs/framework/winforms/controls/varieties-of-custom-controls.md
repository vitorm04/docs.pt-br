---
title: Variedades de controles personalizados
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], user controls
- controls [Windows Forms], types of
- composite controls [Windows Forms]
- extended controls [Windows Forms]
- controls [Windows Forms], extended
- user controls [Windows Forms]
- custom controls [Windows Forms]
- controls [Windows Forms], composite
ms.assetid: 3cea09e5-4344-4ccb-9858-b66ccac210ff
ms.openlocfilehash: 71b71dc992497fda25a5e9453affc7bea98141d7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651552"
---
# <a name="varieties-of-custom-controls"></a>Variedades de controles personalizados
Com o .NET Framework, você pode desenvolver e implementar novos controles. Você pode estender a funcionalidade do controle de usuário familiar, além dos controles existentes, por herança. Você também pode escrever controles personalizados que executam suas próprias pinturas.  
  
 Decidir qual tipo de controle criar pode ser confuso. Este tópico destaca as diferenças entre os vários tipos de controles dos quais você pode herdar e fornece informações sobre como escolher um tipo específico de controle para seu projeto.  
  
> [!NOTE]
>  Para obter informações sobre a criação de um controle para usar no Web Forms, consulte [Desenvolvendo controles de servidores ASP.NET personalizados](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).  
  
## <a name="base-control-class"></a>Classe de controle base  
 O <xref:System.Windows.Forms.Control> é a classe base para controles de formulários do Windows. Ela fornece a infraestrutura necessária para exibição visual em aplicativos Windows Forms.  
  
 O <xref:System.Windows.Forms.Control> classe executa as seguintes tarefas para fornecer uma exibição visual em aplicativos do Windows Forms:  
  
- Expõe um identificador de janela.  
  
- Gerencia o roteamento de mensagens.  
  
- Fornece eventos de teclado e mouse, além de muitos outros eventos da interface do usuário.  
  
- Fornece recursos de layout avançados.  
  
- Contém muitas propriedades específicas para a exibição visual, como <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, e <xref:System.Windows.Forms.Control.Width%2A>.  
  
- Fornece a segurança e o suporte a threading necessários para um controle dos Windows Forms atuar como um controle do Microsoft® ActiveX®.  
  
 Como grande parte da infraestrutura é fornecida pela classe base, é relativamente fácil desenvolver seus próprios controles dos Windows Forms.  
  
## <a name="kinds-of-controls"></a>Tipos de controles  
 O Windows Forms dá suporte a três tipos de controles definidos pelo usuário: *composição*, *estendido* e *personalizado*. As seções a seguir descrevem cada tipo de controle e fornecem recomendações para escolher o tipo para usar em seus projetos.  
  
### <a name="composite-controls"></a>Controles de composição  
 Um controle de composição é uma coleção de controles dos Windows Forms encapsulados em um contêiner comum. Esse tipo de controle é, às vezes, chamado de *controle de usuário*. Os controles contidos são chamados *controles constituintes*.  
  
 Um controle de composição contém todas as funcionalidades inerentes associadas a cada um dos controles dos Windows Forms contidos e permite que você exponha seletivamente e associe suas propriedades. Um controle de composição também é ideal para a funcionalidade de manipulação do teclado padrão sem nenhum esforço adicional de desenvolvimento de sua parte.  
  
 Por exemplo, um controle de composição poderia ser criado para exibir dados de endereço de cliente de um banco de dados. Esse controle pode incluir um <xref:System.Windows.Forms.DataGridView> controle para exibir os campos de banco de dados, uma <xref:System.Windows.Forms.BindingSource> para lidar com a associação a uma fonte de dados e um <xref:System.Windows.Forms.BindingNavigator> controle para percorrer os registros. Você pode expor seletivamente propriedades de vinculação de dados, além de poder empacotar e reutilizar todo o controle do aplicativo para o aplicativo. Para obter um exemplo desse tipo de controle de composição, consulte [como: Aplicar atributos em controles dos Windows Forms](how-to-apply-attributes-in-windows-forms-controls.md).  
  
 Para criar um controle composto, derivam o <xref:System.Windows.Forms.UserControl> classe. O <xref:System.Windows.Forms.UserControl> classe base fornece o roteamento de teclado para controles filho e permite que os controles filho funcionem como um grupo. Para obter mais informações, consulte [Desenvolvendo um controle composto do Windows Forms](developing-a-composite-windows-forms-control.md).  
  
 **Recomendação**  
  
 Herdar o <xref:System.Windows.Forms.UserControl> classe se:  
  
- Você deseja combinar a funcionalidade de vários controles dos Windows Forms em uma única unidade reutilizável.  
  
### <a name="extended-controls"></a>Controles estendidos  
 Você pode derivar um controle herdado de qualquer controle Windows Forms existente. Com essa abordagem, você pode reter todas as funcionalidades inerentes de um controle Windows Forms e estender essa funcionalidade adicionando propriedades personalizadas, métodos ou outros recursos. Com essa opção, você pode substituir a lógica de pintura do controle base e estender a interface do usuário alterando sua aparência.  
  
 Por exemplo, você pode criar um controle derivado de <xref:System.Windows.Forms.Button> controle que controla quantas vezes um usuário clicou nele.  
  
 Em alguns controles, você também pode adicionar uma aparência personalizada para a interface gráfica do usuário do seu controle substituindo o <xref:System.Windows.Forms.Control.OnPaint%2A> método da classe base. Para um botão estendido que rastreia cliques, você pode substituir a <xref:System.Windows.Forms.Control.OnPaint%2A> método para chamar a implementação base de <xref:System.Windows.Forms.Control.OnPaint%2A>e, em seguida, desenhe a contagem de cliques em um canto do <xref:System.Windows.Forms.Button> área de cliente do controle.  
  
 **Recomendação**  
  
 Herde de um controle dos Windows Forms se:  
  
- A maioria da funcionalidade que você precisa já é idêntica a um controle Windows Forms existente.  
  
- Você não precisa de uma interface gráfica do usuário personalizada ou deseja criar uma nova interface gráfica do usuário para um controle existente.  
  
### <a name="custom-controls"></a>Controles personalizados  
 Outra maneira de criar um controle é criar um substancialmente desde o início herdando de <xref:System.Windows.Forms.Control>. O <xref:System.Windows.Forms.Control> classe fornece toda a funcionalidade básica necessária pelos controles, incluindo o mouse e teclado, manipulação de eventos, mas nenhuma funcionalidade específica do controle ou interface gráfica.  
  
 Criando um controle herdando a <xref:System.Windows.Forms.Control> classe requer muito mais ponderamento e esforço que herdar de <xref:System.Windows.Forms.UserControl> ou um controle Windows Forms existente. Como uma grande quantidade de implementação é deixada para você, o controle pode ter maior flexibilidade do que um controle de composição ou estendido e você pode personalizar o controle para atender às suas necessidades.  
  
 Para implementar um controle personalizado, você deve escrever código para o <xref:System.Windows.Forms.Control.OnPaint%2A> eventos de controle, bem como qualquer código específico de recurso necessário. Você também pode substituir o <xref:System.Windows.Forms.Control.WndProc%2A> diretamente mensagens método e o identificador do windows. Essa é a maneira mais eficiente para criar um controle, mas, para usar essa técnica com eficiência, você precisa estar familiarizado com a API do Win32® da Microsoft.  
  
 Um exemplo de um controle personalizado é um controle de relógio que duplica a aparência e o comportamento de um relógio analógico. A pintura personalizada é invocada para fazer com que os ponteiros do relógio se movam em resposta às <xref:System.Windows.Forms.Timer.Tick> eventos de interno <xref:System.Windows.Forms.Timer> componente. Para obter mais informações, confira [Como: Desenvolver um controle de formulários do Windows simples](how-to-develop-a-simple-windows-forms-control.md).  
  
 **Recomendação**  
  
 Herdar o <xref:System.Windows.Forms.Control> classe se:  
  
- Você deseja fornecer uma representação gráfica personalizada do seu controle.  
  
- Você precisa implementar a funcionalidade personalizada que não está disponível por controles padrão.  
  
### <a name="activex-controls"></a>Controles ActiveX  
 Embora a infraestrutura dos Windows Forms tenha sido otimizada para hospedar controles dos Windows Forms, você ainda poderá usar controles ActiveX. Há suporte para esta tarefa no Visual Studio. Para obter mais informações, confira [Como: Adicionar controles ActiveX ao Windows Forms](how-to-add-activex-controls-to-windows-forms.md).  
  
### <a name="windowless-controls"></a>Controles sem janelas  
 As tecnologias ActiveX e Microsoft Visual Basic® 6.0 dão suporte a controles *sem janelas*. Os controles sem janelas não têm suporte nos Windows Forms.  
  
## <a name="custom-design-experience"></a>Experiência de design personalizado  
 Se você precisar implementar uma experiência de tempo de design personalizada, você poderá criar seu próprio designer. Para controles de composição, derive sua classe de designer personalizado do <xref:System.Windows.Forms.Design.ParentControlDesigner> ou o <xref:System.Windows.Forms.Design.DocumentDesigner> classes. Para controles estendidos e personalizados, derive sua classe de designer personalizado do <xref:System.Windows.Forms.Design.ControlDesigner> classe.  
  
 Use o <xref:System.ComponentModel.DesignerAttribute> para associar o controle a seu designer. Para obter mais informações, consulte [estendendo o suporte de tempo de Design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)) e [como: Criar um controle de formulários do Windows que aproveita os recursos de tempo de Design do](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).  
  
## <a name="see-also"></a>Consulte também

- [Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework](developing-custom-windows-forms-controls.md)
- [Como: Desenvolver um controle de formulários do Windows simples](how-to-develop-a-simple-windows-forms-control.md)
- [Desenvolvendo um controle de composição dos Windows Forms](developing-a-composite-windows-forms-control.md)
- [Estendendo o suporte ao tempo de design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Como: Criar um controle de formulários do Windows que tira proveito dos recursos de tempo de Design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))
