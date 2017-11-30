---
title: "Como especificar o contexto de segurança para serviços"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 50a9c6ff7f02cda4475aa5390181fa5d410af161
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-security-context-for-services"></a>Como especificar o contexto de segurança para serviços
Por padrão, os serviços executados em um contexto de segurança diferente do que o usuário que fez logon. Os serviços são executados no contexto da conta padrão do sistema, chamado `LocalSystem`, que oferece diferentes privilégios de acesso a recursos do sistema que o usuário. Você pode alterar esse comportamento para especificar outra conta de usuário sob a qual o serviço deve ser executado.  
  
 Você define o contexto de segurança manipulando o <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> propriedade para o processo no qual o serviço é executado. Essa propriedade permite que você defina o serviço como um dos quatro tipos de conta:  
  
-   `User`, que faz com que o sistema solicitar um nome de usuário válido e uma senha quando o serviço é instalado e executado no contexto de uma conta especificada por um único usuário na rede.  
  
-   `LocalService`, que é executado no contexto de uma conta que atua como um usuário sem privilégios no computador local e apresenta credenciais anônimas para qualquer servidor remoto.  
  
-   `LocalSystem`, que é executado no contexto de uma conta que fornece abrangentes privilégios locais e apresenta as credenciais do computador para qualquer servidor remoto.  
  
-   `NetworkService`, que é executado no contexto de uma conta que atua como um usuário sem privilégios no computador local e apresenta as credenciais do computador para qualquer servidor remoto.  
  
 Para obter mais informações, consulte a enumeração <xref:System.ServiceProcess.ServiceAccount>.  
  
### <a name="to-specify-the-security-context-for-a-service"></a>Para especificar o contexto de segurança para um serviço  
  
1.  Depois de criar seu serviço, adicione os instaladores necessários para ele. Para obter mais informações, consulte [como: adicionar instaladores ao seu aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
2.  No designer, acesse o `ProjectInstaller` classe e clique no instalador do processo de serviço para o serviço que você está trabalhando.  
  
    > [!NOTE]
    >  Para cada aplicativo de serviço, há pelo menos dois componentes de instalação no `ProjectInstaller` classe — uma que instala os processos para todos os serviços no projeto e um instalador para cada serviço que contém o aplicativo. Nesse caso, você deseja selecionar <xref:System.ServiceProcess.ServiceProcessInstaller>.  
  
3.  No **propriedades** janela, defina o <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> para o valor apropriado.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução aos aplicativos de serviço do Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Como: adicionar instaladores ao seu aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Como: criar serviços do Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
