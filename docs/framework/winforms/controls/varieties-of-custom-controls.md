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
ms.openlocfilehash: 106da550fc6e6c50bc40e103e1f855059a9ffa9c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950088"
---
# <a name="varieties-of-custom-controls"></a>Variedades de controles personalizados
Com o .NET Framework, você pode desenvolver e implementar novos controles. Você pode estender a funcionalidade do controle de usuário familiar, além dos controles existentes, por herança. Você também pode escrever controles personalizados que executam suas próprias pinturas.  
  
 Decidir qual tipo de controle criar pode ser confuso. Este tópico destaca as diferenças entre os vários tipos de controles dos quais você pode herdar e fornece informações sobre como escolher um tipo específico de controle para seu projeto.  
  
> [!NOTE]
> Para obter informações sobre a criação de um controle para usar no Web Forms, consulte [Desenvolvendo controles de servidores ASP.NET personalizados](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).  
  
## <a name="base-control-class"></a>Classe de controle base  
 A <xref:System.Windows.Forms.Control> classe é a classe base para controles de Windows Forms. Ela fornece a infraestrutura necessária para exibição visual em aplicativos Windows Forms.  
  
 A <xref:System.Windows.Forms.Control> classe executa as seguintes tarefas para fornecer exibição Visual em aplicativos Windows Forms:  
  
- Expõe um identificador de janela.  
  
- Gerencia o roteamento de mensagens.  
  
- Fornece eventos de teclado e mouse, além de muitos outros eventos da interface do usuário.  
  
- Fornece recursos de layout avançados.  
  
- Contém muitas propriedades específicas para a exibição Visual, como <xref:System.Windows.Forms.Control.ForeColor%2A> <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, e <xref:System.Windows.Forms.Control.Width%2A>.  
  
- Fornece a segurança e o suporte a threading necessários para um controle dos Windows Forms atuar como um controle do Microsoft® ActiveX®.  
  
 Como grande parte da infraestrutura é fornecida pela classe base, é relativamente fácil desenvolver seus próprios controles dos Windows Forms.  
  
## <a name="kinds-of-controls"></a>Tipos de controles  
 O Windows Forms dá suporte a três tipos de controles definidos pelo usuário: *composição*, *estendido* e *personalizado*. As seções a seguir descrevem cada tipo de controle e fornecem recomendações para escolher o tipo para usar em seus projetos.  
  
### <a name="composite-controls"></a>Controles de composição  
 Um controle de composição é uma coleção de controles dos Windows Forms encapsulados em um contêiner comum. Esse tipo de controle é, às vezes, chamado de *controle de usuário*. Os controles contidos são chamados *controles constituintes*.  
  
 Um controle de composição contém todas as funcionalidades inerentes associadas a cada um dos controles dos Windows Forms contidos e permite que você exponha seletivamente e associe suas propriedades. Um controle de composição também é ideal para a funcionalidade de manipulação do teclado padrão sem nenhum esforço adicional de desenvolvimento de sua parte.  
  
 Por exemplo, um controle de composição poderia ser criado para exibir dados de endereço de cliente de um banco de dados. Esse controle pode incluir um <xref:System.Windows.Forms.DataGridView> controle para exibir os campos do banco de <xref:System.Windows.Forms.BindingSource> dados, um para lidar com a associação a uma <xref:System.Windows.Forms.BindingNavigator> fonte, e um controle para percorrer os registros. Você pode expor seletivamente propriedades de vinculação de dados, além de poder empacotar e reutilizar todo o controle do aplicativo para o aplicativo. Para obter um exemplo desse tipo de controle composto, consulte [como: Aplicar atributos em controles](how-to-apply-attributes-in-windows-forms-controls.md)de Windows Forms.  
  
 Para criar um controle composto, derive da <xref:System.Windows.Forms.UserControl> classe. A <xref:System.Windows.Forms.UserControl> classe base fornece roteamento de teclado para controles filho e permite que controles filho funcionem como um grupo. Para obter mais informações, consulte [Desenvolvendo um controle composto do Windows Forms](developing-a-composite-windows-forms-control.md).  
  
 **Recomendação**  
  
 Herdar da <xref:System.Windows.Forms.UserControl> classe se:  
  
- Você deseja combinar a funcionalidade de vários controles dos Windows Forms em uma única unidade reutilizável.  
  
### <a name="extended-controls"></a>Controles estendidos  
 Você pode derivar um controle herdado de qualquer controle Windows Forms existente. Com essa abordagem, você pode reter todas as funcionalidades inerentes de um controle Windows Forms e estender essa funcionalidade adicionando propriedades personalizadas, métodos ou outros recursos. Com essa opção, você pode substituir a lógica de pintura do controle base e estender a interface do usuário alterando sua aparência.  
  
 Por exemplo, você pode criar um controle derivado do <xref:System.Windows.Forms.Button> controle que controla quantas vezes um usuário clicou nele.  
  
 Em alguns controles, você também pode adicionar uma aparência personalizada à interface gráfica do usuário do seu controle, substituindo <xref:System.Windows.Forms.Control.OnPaint%2A> o método da classe base. Para um botão estendido que controla cliques, você pode substituir <xref:System.Windows.Forms.Control.OnPaint%2A> o método para chamar a implementação base <xref:System.Windows.Forms.Control.OnPaint%2A>de e, em seguida, desenhar a contagem de cliques <xref:System.Windows.Forms.Button> em um canto da área do cliente do controle.  
  
 **Recomendação**  
  
 Herde de um controle dos Windows Forms se:  
  
- A maioria da funcionalidade que você precisa já é idêntica a um controle Windows Forms existente.  
  
- Você não precisa de uma interface gráfica do usuário personalizada ou deseja criar uma nova interface gráfica do usuário para um controle existente.  
  
### <a name="custom-controls"></a>Controles personalizados  
 Outra maneira de criar um controle é criar um substancialmente desde o início, herdando de <xref:System.Windows.Forms.Control>. A <xref:System.Windows.Forms.Control> classe fornece toda a funcionalidade básica exigida pelos controles, incluindo eventos de manipulação de mouse e teclado, mas nenhuma funcionalidade específica de controle ou interface gráfica.  
  
 A <xref:System.Windows.Forms.Control> criação de um controle por herança da classe requer muito mais pensamento e esforço do que a herança <xref:System.Windows.Forms.UserControl> de um controle de Windows Forms existente. Como uma grande quantidade de implementação é deixada para você, o controle pode ter maior flexibilidade do que um controle de composição ou estendido e você pode personalizar o controle para atender às suas necessidades.  
  
 Para implementar um controle personalizado, você deve escrever código para o <xref:System.Windows.Forms.Control.OnPaint%2A> evento do controle, bem como qualquer código específico de recurso que você precise. Você também pode substituir o <xref:System.Windows.Forms.Control.WndProc%2A> método e tratar as mensagens do Windows diretamente. Essa é a maneira mais eficiente para criar um controle, mas, para usar essa técnica com eficiência, você precisa estar familiarizado com a API do Win32® da Microsoft.  
  
 Um exemplo de um controle personalizado é um controle de relógio que duplica a aparência e o comportamento de um relógio analógico. A pintura personalizada é chamada para fazer com que as mãos do relógio sejam movidas em resposta <xref:System.Windows.Forms.Timer.Tick> a <xref:System.Windows.Forms.Timer> eventos de um componente interno. Para obter mais informações, confira [Como: Desenvolva um controle](how-to-develop-a-simple-windows-forms-control.md)simples de Windows Forms.  
  
 **Recomendação**  
  
 Herdar da <xref:System.Windows.Forms.Control> classe se:  
  
- Você deseja fornecer uma representação gráfica personalizada do seu controle.  
  
- Você precisa implementar a funcionalidade personalizada que não está disponível por controles padrão.  
  
### <a name="activex-controls"></a>Controles ActiveX  
 Embora a infraestrutura dos Windows Forms tenha sido otimizada para hospedar controles dos Windows Forms, você ainda poderá usar controles ActiveX. Há suporte para esta tarefa no Visual Studio. Para obter mais informações, confira [Como: Adicione controles ActiveX a Windows Forms](how-to-add-activex-controls-to-windows-forms.md).  
  
### <a name="windowless-controls"></a>Controles sem janelas  
 As tecnologias ActiveX e Microsoft Visual Basic® 6.0 dão suporte a controles *sem janelas*. Os controles sem janelas não têm suporte nos Windows Forms.  
  
## <a name="custom-design-experience"></a>Experiência de design personalizado  
 Se você precisar implementar uma experiência de tempo de design personalizada, você poderá criar seu próprio designer. Para controles de composição, derive sua classe de designer <xref:System.Windows.Forms.Design.ParentControlDesigner> personalizada das <xref:System.Windows.Forms.Design.DocumentDesigner> classes ou. Para controles estendidos e personalizados, derive sua classe de designer <xref:System.Windows.Forms.Design.ControlDesigner> personalizada da classe.  
  
 Use o <xref:System.ComponentModel.DesignerAttribute> para associar seu controle com seu designer. Para obter mais informações, consulte Estendendo o [suporte ao tempo de design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)) e [como: Crie um controle de Windows Forms que aproveita os recursos](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))de tempo de design.  
  
## <a name="see-also"></a>Consulte também

- [Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework](developing-custom-windows-forms-controls.md)
- [Como: Desenvolver um controle de Windows Forms simples](how-to-develop-a-simple-windows-forms-control.md)
- [Desenvolvendo um controle de composição dos Windows Forms](developing-a-composite-windows-forms-control.md)
- [Estendendo o suporte ao tempo de design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Como: Criar um controle de Windows Forms que aproveita os recursos de tempo de design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))
