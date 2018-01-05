---
title: Representando e revertendo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET Framework], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 869b9aadfa236a39d9807062e61046922e382d13
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="impersonating-and-reverting"></a>Representando e revertendo
Às vezes, você precisará obter um token de conta do Windows para representar uma conta do Windows. Por exemplo, seu aplicativo baseado no ASP.NET talvez precise atuar em nome de vários usuários em momentos diferentes. Seu aplicativo pode aceitar um token que representa um administrador de serviços de informações da Internet (IIS), representar o usuário, executar uma operação e reverter para a identidade anterior. Em seguida, ele pode aceitar um token do IIS que representa um usuário com direitos de menos, executar alguma operação e reverter novamente.  
  
 Em situações em que seu aplicativo deve representar uma conta do Windows que não tenha sido anexada ao segmento atual pelo IIS, você deve recuperar o token da conta e usá-la para ativar a conta. Você pode fazer isso executando as seguintes tarefas:  
  
1.  Recuperar um token de conta para um usuário específico, fazendo uma chamada de gerenciado para não gerenciado **LogonUser** método. Este método não está na biblioteca de classe base do .NET Framework, mas está localizado no não gerenciado **Advapi32**. Acessar os métodos no código não gerenciado é uma operação avançada e está além do escopo desta discussão. Para obter mais informações, consulte [interoperação com código não gerenciado](../../../docs/framework/interop/index.md). Para obter mais informações sobre o **LogonUser** método e **Advapi32**, consulte a documentação do SDK da plataforma.  
  
2.  Criar uma nova instância do **WindowsIdentity** classe, passando o token. O código a seguir demonstra essa chamada, onde `hToken` representa um token do Windows.  
  
    ```csharp  
    WindowsIdentity ImpersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim ImpersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3.  Começar a representação, criando uma nova instância do <xref:System.Security.Principal.WindowsImpersonationContext> classe e inicializá-la com o <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> método da classe inicializado, conforme mostrado no código a seguir.  
  
    ```csharp  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate()  
    ```  
  
4.  Quando você não precisa representar, chame o <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> método para reverter a representação, conforme mostrado no código a seguir.  
  
    ```csharp  
    MyImpersonation.Undo();  
    ```  
  
    ```vb  
    MyImpersonation.Undo()  
    ```  
  
 Se confiável código já anexou um <xref:System.Security.Principal.WindowsPrincipal> do objeto para o thread, você pode chamar o método de instância **representar**, que não tem um token de conta. Observe que isso é útil somente quando o **WindowsPrincipal** objeto no thread representa um usuário diferente em que o processo está em execução atualmente. Por exemplo, você pode encontrar essa situação usando ASP.NET com autenticação do Windows ativado e desativado de representação. Nesse caso, o processo é executado sob uma conta configurada em serviços de informações da Internet (IIS), enquanto o servidor principal atual representa o usuário do Windows que está acessando a página.  
  
 Observe que nem **representar** nem **desfazer** alterações a **Principal** objeto (<xref:System.Security.Principal.IPrincipal>) associado ao contexto atual de chamada. Em vez disso, representação e alteração de reverter o token associado ao processo do sistema operacional atual.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Security.Principal.WindowsIdentity>  
 <xref:System.Security.Principal.WindowsImpersonationContext>  
 [Objetos Principal e Identity](../../../docs/standard/security/principal-and-identity-objects.md)  
 [Interoperação com código não gerenciado](../../../docs/framework/interop/index.md)
