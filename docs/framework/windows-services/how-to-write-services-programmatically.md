---
title: 'Como: Escrever serviços de forma programática'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
author: ghogen
ms.openlocfilehash: 29e0b95ad91c93f3a23246daf2be128b10d7e2ce
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952401"
---
# <a name="how-to-write-services-programmatically"></a>Como: Escrever serviços de forma programática
Quando você opta por não usar o modelo de projeto de Serviço Windows, é possível escrever seus próprios serviços configurando a herança e outros elementos de infraestrutura por conta própria. Ao criar um serviço de forma programática, você precisa executar várias etapas que o modelo executaria para você:  
  
- Você precisa configurar a classe de serviço para ser herdada da classe <xref:System.ServiceProcess.ServiceBase>.  
  
- Você precisa criar um método `Main` para seu projeto de serviço que defina os serviços a serem executados e chame o método <xref:System.ServiceProcess.ServiceBase.Run%2A>neles.  
  
- Você precisa substituir os procedimentos <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e <xref:System.ServiceProcess.ServiceBase.OnStop%2A> e preencher os códigos que desejar que eles executem.  
  
### <a name="to-write-a-service-programmatically"></a>Para escrever um serviço de forma programático  
  
1. Criar um projeto vazio e crie uma referência aos namespaces necessários seguindo estas etapas:  
  
    1. Em **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Referências** e clique em **Adicionar Referência**.  
  
    2. Na guia **.NET Framework**, role até **System.dll** e clique em **Selecionar**.  
  
    3. Role até **System.ServiceProcess.dll** e clique em **Selecionar**.  
  
    4. Clique em **OK**.  
  
2. Adicione uma classe e configure-a para ser herdada de <xref:System.ServiceProcess.ServiceBase>:  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3. Adicione o código a seguir para configurar sua classe de serviço:  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4. Crie um método `Main` para sua classe e use-o para definir o serviço que a classe conterá. `userService1` é o nome da classe:  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5. Substitua o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e defina o processamento que deverá ocorrer quando o serviço for iniciado.  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6. Substitua quaisquer outros métodos para os quais deseje definir um processamento personalizado e escreva o código para determinar as ações que o serviço deve executar em cada caso.  
  
7. Adicionar os instaladores necessários para seu aplicativo de serviço. Para obter mais informações, confira [Como: Adicionar instaladores ao aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
8. Compile o projeto selecionando **Compilar Solução** no menu **Compilar**.  
  
    > [!NOTE]
    > Pressione F5 para executar seu projeto. Você não pode executar um projeto de serviço dessa maneira.  
  
9. Crie um projeto de instalação e as ações personalizadas para instalar o serviço. Para obter um exemplo, confira [Passo a passo: criando um aplicativo de serviço Windows no Designer de Componentes](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
10. Instale o serviço. Para obter mais informações, confira [Como: Instalar e desinstalar serviços](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Consulte também

- [Introdução aos Aplicativos de Serviço Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Como: criar serviços do Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [Como: adicionar instaladores ao aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [Como: Registrar em log informações sobre serviços](../../../docs/framework/windows-services/how-to-log-information-about-services.md)
- [Passo a passo: Criando um aplicativo de serviço Windows no Designer de Componentes](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
