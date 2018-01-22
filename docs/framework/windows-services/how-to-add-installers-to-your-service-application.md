---
title: "Como adicionar instaladores ao aplicativo de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, deploying
- installation components, adding to services
- installers, adding to services
- Windows Service applications, adding installers
- services, adding installers
- ServiceInstaller class, adding installers to services
- ServiceProcessInstaller class, adding installers to services
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
caps.latest.revision: "14"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 15487d4311f896aa09c1c7712292058086a49b50
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-installers-to-your-service-application"></a>Como adicionar instaladores ao aplicativo de serviço
O Visual Studio possui componentes de instalação que podem instalar recursos associados com seus aplicativos de serviço. Componentes de instalação registram um serviço individual no sistema ao qual ele está sendo instalado e informe o Gerenciador de controle de serviços que o serviço existe. Quando você trabalha com um aplicativo de serviço, você pode selecionar um link na janela Propriedades para adicionar automaticamente os instaladores apropriados ao seu projeto.  
  
> [!NOTE]
>  Valores de propriedade para o serviço são copiados da classe de serviço para a classe de instalador. Se você atualizar os valores de propriedade na classe de serviço, eles não são atualizados automaticamente no instalador.  
  
 Quando você adiciona um instalador para seu projeto, uma nova classe (que, por padrão, é chamado `ProjectInstaller`) é criado no projeto e instâncias da instalação apropriada componentes são criados dentro dele. Esta classe age como um ponto central para todos os componentes de instalação precisa de seu projeto. Por exemplo, se você adicionar um segundo serviço para seu aplicativo e clique no link Adicionar instalador, uma segunda classe de instalador não é criada; em vez disso, o componente de instalação adicional necessário para o segundo serviço é adicionado à classe existente.  
  
 Você não precisa fazer qualquer codificação especial dentro dos instaladores para fazer seus serviços instalarem corretamente. No entanto, ocasionalmente, convém modificar o conteúdo dos instaladores se você precisa adicionar uma funcionalidade especial para o processo de instalação.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-installers-to-your-service-application"></a>Para adicionar instaladores ao seu aplicativo de serviço  
  
1.  Em **Solution Explorer**, acesso **Design** exibição para o serviço para o qual você deseja adicionar um componente de instalação.  
  
2.  Clique em plano de fundo do designer para selecionar o serviço propriamente dito, em vez de um de seus conteúdos.  
  
3.  Com o designer em foco, o botão direito do mouse e clique **adicionar instalador**.  
  
     Uma nova classe, `ProjectInstaller`e dois componentes de instalação, <xref:System.ServiceProcess.ServiceProcessInstaller> e <xref:System.ServiceProcess.ServiceInstaller>, são adicionados ao seu projeto e valores de propriedade para o serviço são copiados para os componentes.  
  
4.  Clique o <xref:System.ServiceProcess.ServiceInstaller> componente e verificar se o valor da <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> propriedade é definida como o mesmo valor que o <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> propriedade no próprio serviço.  
  
5.  Para determinar como seu serviço será iniciado, clique o <xref:System.ServiceProcess.ServiceInstaller> componente e defina o <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> propriedade para o valor apropriado.  
  
    |Valor|Resultado|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|O serviço deve ser iniciado manualmente após a instalação. Para obter mais informações, consulte [como: iniciar os serviços](../../../docs/framework/windows-services/how-to-start-services.md).|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|O serviço será iniciado por si só, sempre que o computador é reinicializado.|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|Não é possível iniciar o serviço.|  
  
6.  Para determinar o contexto de segurança no qual seu serviço será executado, clique o <xref:System.ServiceProcess.ServiceProcessInstaller> componente e defina os valores de propriedade apropriada. Para obter mais informações, consulte [como: especificar o contexto de segurança para serviços](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md).  
  
7.  Substitua todos os métodos para os quais você precisa realizar processamento personalizado.  
  
8.  Execute as etapas 1 a 7 para cada serviço adicional em seu projeto.  
  
    > [!NOTE]
    >  Para cada serviço adicional em seu projeto, você deve adicionar adicional <xref:System.ServiceProcess.ServiceInstaller> componente para o projeto `ProjectInstaller` classe. O <xref:System.ServiceProcess.ServiceProcessInstaller> componente adicionado na etapa três funciona com todos os instaladores de serviço individuais no projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução aos Aplicativos de Serviço Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Como instalar e desinstalar serviços](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [Como iniciar serviços](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Como especificar o contexto de segurança para serviços](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)
