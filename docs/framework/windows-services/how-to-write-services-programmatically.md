---
title: "Como escrever serviços de forma programática"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
caps.latest.revision: "21"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: cdb9c7bba564b71bfba86076218e48610cf73076
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-write-services-programmatically"></a>Como escrever serviços de forma programática
Se você optar por não usar o modelo de projeto de serviço do Windows, você pode escrever seus próprios serviços, configurando a herança e outros elementos de infraestrutura por conta própria. Quando você cria um serviço programaticamente, você deve executar várias etapas que o modelo trataria para você:  
  
-   Você deve configurar sua classe de serviço herde o <xref:System.ServiceProcess.ServiceBase> classe.  
  
-   Você deve criar um `Main` método para seu projeto de serviço que define os serviços a executar e chama o <xref:System.ServiceProcess.ServiceBase.Run%2A> método neles.  
  
-   Você deve substituir o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedimentos e preencha qualquer código que você deseja executá-los.  
  
### <a name="to-write-a-service-programmatically"></a>Escrever um serviço por meio de programação  
  
1.  Criar um projeto vazio e criar uma referência aos namespaces necessários seguindo estas etapas:  
  
    1.  Em **Solution Explorer**, com o botão direito do **referências** nó e clique em **adicionar referência**.  
  
    2.  Sobre o **do .NET Framework** guia, role até **System.dll** e clique em **selecione**.  
  
    3.  Role até **System.ServiceProcess.dll** e clique em **selecione**.  
  
    4.  Clique em **OK**.  
  
2.  Adicionar uma classe e configurá-lo para herdar de <xref:System.ServiceProcess.ServiceBase>:  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3.  Adicione o código a seguir para configurar sua classe de serviço:  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4.  Criar um `Main` método para sua classe e usá-lo para definir o serviço que sua classe irá conter; `userService1` é o nome da classe:  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5.  Substituir o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método e defina qualquer processamento que deve ocorrer quando o serviço é iniciado.  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6.  Substitua quaisquer outros métodos que você deseja definir processamento personalizado e escrever código para determinar as ações que o serviço deve tomar em cada caso.  
  
7.  Adicionar os instaladores necessários para seu aplicativo de serviço. Para obter mais informações, consulte [como: adicionar instaladores ao seu aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
8.  Compilar o projeto selecionando **compilar solução** do **criar** menu.  
  
    > [!NOTE]
    >  Pressione F5 para executar seu projeto. Você não pode executar um projeto de serviço dessa maneira.  
  
9. Crie um projeto de instalação e as ações personalizadas para instalar o serviço. Para obter um exemplo, consulte [passo a passo: Criando um aplicativo de serviço do Windows no Designer de componente](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
10. Instale o serviço. Para obter mais informações, consulte [como: instalar e desinstalar serviços](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Consulte também  
 [Introdução aos Aplicativos de Serviço Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Como criar Serviços do Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Como adicionar instaladores no seu aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Como registrar informações sobre serviços](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [Passo a passo: criando um aplicativo de Serviço Windows no Designer de componentes](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
