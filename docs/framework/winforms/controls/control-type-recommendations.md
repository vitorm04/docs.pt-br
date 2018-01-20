---
title: "Recomendações do tipo de controle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- user controls [Windows Forms], when to use
- custom controls [Windows Forms], types
- controls [Windows Forms], creating
ms.assetid: 5235fe9d-c36a-4c08-ae76-6cb90b50085e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a126d3b21ddd4bd31e168726c3538de21fb7d956
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="control-type-recommendations"></a>Recomendações do tipo de controle
O .NET Framework fornece a capacidade de desenvolver e implementar novos controles. Além do controle de usuário familiar, agora você poderá gravar controles personalizados que executam sua os que executam suas próprias pinturas e que podem até mesmo estender as funcionalidades de controles existentes por meio de herança. Decidindo qual tipo de controle criar pode ser confuso. Esta seção destaca as diferenças entre os vários tipos de controles pelos quais você pode herdar e fornece considerações relacionadas ao tipo que você escolher para seu projeto.  
  
> [!NOTE]
>  Caso queira criar um controle para usar no Web Forms, consulte [Desenvolvendo Controles de Servidores ASP.NET Personalizados](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
  
## <a name="inheriting-from-a-windows-forms-control"></a>Herdando de um controle dos Windows Forms  
 Você pode derivar um controle herdado de qualquer controle Windows Forms existente. Essa abordagem permite a você reter todas as funcionalidades inerentes de um controle Windows Forms e estender essa funcionalidade adicionando propriedades personalizadas, métodos ou outras funcionalidades. Por exemplo, você pode criar um controle derivado de <xref:System.Windows.Forms.TextBox> que pode aceitar apenas números e converte a entrada em um valor automaticamente. Um controle desse tipo pode conter código de validação que foi chamado sempre que o texto na caixa de texto foi alterado e pode ter uma propriedade adicional, Valor. Em alguns controles, você também pode adicionar uma aparência personalizada para a interface gráfica do seu controle substituindo o <xref:System.Windows.Forms.Control.OnPaint%2A> método da classe base.  
  
 Herde de um controle dos Windows Forms se:  
  
-   A maioria da funcionalidade que você precisa já é idêntica a um controle Windows Forms existente.  
  
-   Você não precisa de uma interface gráfica personalizada ou deseja criar um novo front-end gráfico para um controle existente.  
  
## <a name="inheriting-from-the-usercontrol-class"></a>Herdando da classe UserControl  
 Um controle de usuário é uma coleção de controles dos Windows Forms encapsulados em um contêiner comum. Um contêiner contém todas as funcionalidades inerentes associadas a cada um dos controles dos Windows Forms e permite que você exponha seletivamente e associe suas propriedades. Um exemplo de um controle composto poderia ser um controle criado para exibir dados de endereço de cliente de um banco de dados. Esse controle incluiria várias caixas de texto para exibir cada campo e controles de botão para navegar pelos registros. Você pode expor seletivamente propriedades de associação de dados, além de poder empacotar e reutilizar todo o controle do aplicativo para o aplicativo.  
  
 Herdam o <xref:System.Windows.Forms.UserControl> classe se:  
  
-   Você deseja combinar a funcionalidade de vários controles dos Windows Forms em uma única unidade reutilizável.  
  
## <a name="inheriting-from-the-control-class"></a>Herdando da Classe de Controle  
 Outra maneira de criar um controle é criar um do zero herdando de <xref:System.Windows.Forms.Control>. O <xref:System.Windows.Forms.Control> classe fornece toda a funcionalidade básica necessária por controles (por exemplo, eventos), mas nenhuma funcionalidade específica de controle ou interface gráfica. Criando um controle, herdando a <xref:System.Windows.Forms.Control> classe requer muito mais pensamento e o esforço que herdando um controle de formulários do Windows existente ou controle de usuário. O autor deve escrever o código para o <xref:System.Windows.Forms.Control.OnPaint%2A> eventos de controle, bem como qualquer código específico de funcionalidade que é necessária. Maior flexibilidade é permitida, no entanto e você pode personalizar um controle para atender às suas necessidades. Um exemplo de um controle personalizado é um controle de relógio que duplica a aparência e a ação de um relógio analógico. Pintura personalizada seria invocada para fazer com que os ponteiros do relógio para mover em resposta a <xref:System.Windows.Forms.Timer.Tick> eventos de um componente de temporizador internos.  
  
 Herdam o <xref:System.Windows.Forms.Control> classe se:  
  
-   Você deseja fornecer uma representação gráfica personalizada do seu controle.  
  
-   Você precisa implementar a funcionalidade personalizada que não está disponível por controles padrão.  
  
-   [Como exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))  
  
-   [Passo a passo: serializando coleções de tipos padrão com DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))  
  
-   [Passo a passo: herdando um controle dos Windows Forms com Visual C#](http://msdn.microsoft.com/library/5h0k2e6x\(v=vs.110\))  
  
-   [Como fornecer um bitmap da caixa de ferramentas para um controle](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))  
  
-   [Como herdar de controles dos Windows Forms existentes](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))  
  
-   [Passo a passo: depurando controles personalizados dos Windows Forms em tempo de Design](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))  
  
-   [Como herdar da classe de controle](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))  
  
-   [Como testar o comportamento de tempo de execução de um UserControl](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))  
  
-   [Como alinhar um controle às bordas de formulários no tempo de design](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))  
  
-   [Como herdar da classe UserControl](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))  
  
-   [Como Criar Controles para o Windows Forms](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))  
  
-   [Como criar controles de composição](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))  
  
-   [Passo a passo: criando um controle de composição com o Visual Basic](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))  
  
-   [Passo a passo: criando um controle de composição com o Visual C#](http://msdn.microsoft.com/library/a6h7e207\(v=vs.110\))  
  
-   [Passo a passo: herdando um controle dos Windows Forms com Visual Basic](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))  
  
-   [Como criar um controle dos Windows Forms que aproveita recursos de tempo de design](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))  
  
-   [Como criar um controle dos Windows Forms que aproveita recursos de tempo de design](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))  
  
## <a name="see-also"></a>Consulte também  
 [Como desenvolver um controle simples dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [Variedades de controles personalizados](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
