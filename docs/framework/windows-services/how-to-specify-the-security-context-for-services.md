---
title: Como especificar o contexto de segurança para serviços
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
author: ghogen
manager: douge
ms.openlocfilehash: e3e5ad7dd44dcaf1593ac80bbe6d0a367964e4e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
 [Introdução aos Aplicativos de Serviço Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Como adicionar instaladores no seu aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Como criar Serviços do Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
