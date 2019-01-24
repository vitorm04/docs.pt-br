---
title: Recomendações do tipo de controle
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- user controls [Windows Forms], when to use
- custom controls [Windows Forms], types
- controls [Windows Forms], creating
ms.assetid: 5235fe9d-c36a-4c08-ae76-6cb90b50085e
ms.openlocfilehash: 5e3337dddcc39517558cf85af76223306d20d2bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599693"
---
# <a name="control-type-recommendations"></a>Recomendações do tipo de controle
O .NET Framework fornece a capacidade de desenvolver e implementar novos controles. Além do controle de usuário familiar, agora você poderá gravar controles personalizados que executam sua os que executam suas próprias pinturas e que podem até mesmo estender as funcionalidades de controles existentes por meio de herança. Decidindo qual tipo de controle criar pode ser confuso. Esta seção destaca as diferenças entre os vários tipos de controles pelos quais você pode herdar e fornece considerações relacionadas ao tipo que você escolher para seu projeto.  
  
> [!NOTE]
>  Caso queira criar um controle para usar no Web Forms, consulte [Desenvolvendo Controles de Servidores ASP.NET Personalizados](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
  
## <a name="inheriting-from-a-windows-forms-control"></a>Herdando de um controle dos Windows Forms  
 Você pode derivar um controle herdado de qualquer controle Windows Forms existente. Essa abordagem permite a você reter todas as funcionalidades inerentes de um controle Windows Forms e estender essa funcionalidade adicionando propriedades personalizadas, métodos ou outras funcionalidades. Por exemplo, você pode criar um controle derivado de <xref:System.Windows.Forms.TextBox> que pode aceitar apenas números e converte automaticamente a entrada em um valor. Um controle desse tipo pode conter código de validação que foi chamado sempre que o texto na caixa de texto foi alterado e pode ter uma propriedade adicional, Valor. Em alguns controles, você também pode adicionar uma aparência personalizada para a interface gráfica do seu controle substituindo o <xref:System.Windows.Forms.Control.OnPaint%2A> método da classe base.  
  
 Herde de um controle dos Windows Forms se:  
  
-   A maioria da funcionalidade que você precisa já é idêntica a um controle Windows Forms existente.  
  
-   Você não precisa de uma interface gráfica personalizada ou deseja criar um novo front-end gráfico para um controle existente.  
  
## <a name="inheriting-from-the-usercontrol-class"></a>Herdando da classe UserControl  
 Um controle de usuário é uma coleção de controles dos Windows Forms encapsulados em um contêiner comum. Um contêiner contém todas as funcionalidades inerentes associadas a cada um dos controles dos Windows Forms e permite que você exponha seletivamente e associe suas propriedades. Um exemplo de um controle composto poderia ser um controle criado para exibir dados de endereço de cliente de um banco de dados. Esse controle incluiria várias caixas de texto para exibir cada campo e controles de botão para navegar pelos registros. Você pode expor seletivamente propriedades de associação de dados, além de poder empacotar e reutilizar todo o controle do aplicativo para o aplicativo.  
  
 Herdar o <xref:System.Windows.Forms.UserControl> classe se:  
  
-   Você deseja combinar a funcionalidade de vários controles dos Windows Forms em uma única unidade reutilizável.  
  
## <a name="inheriting-from-the-control-class"></a>Herdando da Classe de Controle  
 Outra maneira de criar um controle é criar um substancialmente novo herdando de <xref:System.Windows.Forms.Control>. O <xref:System.Windows.Forms.Control> classe fornece toda a funcionalidade básica necessária por controles (por exemplo, eventos), mas nenhuma funcionalidade específica do controle ou interface gráfica. Criando um controle herdando a <xref:System.Windows.Forms.Control> classe requer muito mais ponderamento e esforço que herdar de controle de usuário ou um controle Windows Forms existente. O autor deve gravar código para o <xref:System.Windows.Forms.Control.OnPaint%2A> eventos de controle, bem como qualquer código específico do que é necessário. Maior flexibilidade é permitida, no entanto e você pode personalizar um controle para atender às suas necessidades. Um exemplo de um controle personalizado é um controle de relógio que duplica a aparência e a ação de um relógio analógico. A pintura personalizada deve ser invocada para fazer com que os ponteiros do relógio se movam em resposta a <xref:System.Windows.Forms.Timer.Tick> eventos de um componente de temporizador interno.  
  
 Herdar o <xref:System.Windows.Forms.Control> classe se:  
  
-   Você deseja fornecer uma representação gráfica personalizada do seu controle.  
  
-   Você precisa implementar a funcionalidade personalizada que não está disponível por controles padrão.  
  
-   [Como: Exibir um controle na caixa de diálogo de itens de caixa de ferramentas de escolha](https://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))  
  
-   [Passo a passo: Serializando coleções de tipos padrão com DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)  
  
-   [Passo a passo: Herdando um controle de formulários do Windows com VisualC#](https://msdn.microsoft.com/library/5h0k2e6x\(v=vs.110\))  
  
-   [Como: Fornecer um Bitmap da caixa de ferramentas para um controle](https://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))  
  
-   [Como: Herdar controles de formulários do Windows existentes](https://msdn.microsoft.com/library/7h62478z\(v=vs.110\))  
  
-   [Passo a passo: Depuração de controles personalizados do Windows Forms em tempo de design](https://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))  
  
-   [Como: Herdar da classe de controle](https://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))  
  
-   [Como: Testar o comportamento de tempo de execução de um UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
  
-   [Como: Alinhar um controle às bordas de formulários no tempo de Design](https://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))  
  
-   [Como: Herdar da classe UserControl](https://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))  
  
-   [Como: Criar controles para Windows Forms](https://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))  
  
-   [Como: Criar controles compostos](https://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))  
  
-   [Passo a passo: Criando um controle composto com o Visual Basic](https://msdn.microsoft.com/library/c316f119\(v=vs.110\))  
  
-   [Passo a passo: Criando um controle composto com VisualC#](https://msdn.microsoft.com/library/a6h7e207\(v=vs.110\))  
  
-   [Passo a passo: Herdando um controle de formulários do Windows com o Visual Basic](https://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))  
  
-   [Como: Criar um controle de formulários do Windows que tira proveito dos recursos de tempo de Design](https://msdn.microsoft.com/library/307hck25\(v=vs.110\))  
  
-   [Como: Criar um controle de formulários do Windows que tira proveito dos recursos de tempo de Design](https://msdn.microsoft.com/library/307hck25\(v=vs.120\))  
  
## <a name="see-also"></a>Consulte também
- [Como: Desenvolver um controle de formulários do Windows simples](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)
- [Variedades de controles personalizados](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
