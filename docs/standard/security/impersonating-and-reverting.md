---
title: Representando e revertendo
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET Framework], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 97b15ea2202ca410dd517db63a7145d27f62bb48
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018587"
---
# <a name="impersonating-and-reverting"></a>Representando e revertendo
Às vezes, talvez seja necessário obter um token de conta do Windows para representar uma conta do Windows. Por exemplo, seu aplicativo baseado no ASP.NET pode ter que atuar em nome de vários usuários em momentos diferentes. Seu aplicativo pode aceitar um token que representa um administrador de serviços de informações da Internet (IIS), representar o usuário, executar uma operação e reverter para a identidade anterior. Em seguida, ele pode aceitar um token do IIS que representa um usuário com poucos direitos, executar alguma operação e reverter novamente.  
  
 Em situações em que seu aplicativo deve representar uma conta do Windows que não foi anexada ao thread atual pelo IIS, você deve recuperar o token dessa conta e usá-lo para ativar a conta. Você pode fazer isso executando as seguintes tarefas:  
  
1. Recuperar um token de conta para um usuário específico, fazendo uma chamada não gerenciado **LogonUser** método. Esse método não está na biblioteca de classes base do .NET Framework, mas está localizado no não gerenciado **advapi32.dll**. Acessando os métodos no código não gerenciado é uma operação avançada e está além do escopo desta discussão. Para obter mais informações, consulte [interoperação com código não gerenciado](../../../docs/framework/interop/index.md). Para obter mais informações sobre o **LogonUser** método e **advapi32.dll**, consulte a documentação do SDK da plataforma.  
  
2. Criar uma nova instância dos **WindowsIdentity** classe, passando o token. O código a seguir demonstra essa chamada, onde `hToken` representa um token do Windows.  
  
    ```csharp  
    WindowsIdentity impersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim impersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3. Comece a criar uma nova instância da representação de <xref:System.Security.Principal.WindowsImpersonationContext> classe e inicializá-la com o <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> método da classe inicializada, conforme mostrado no código a seguir.  
  
    ```csharp  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate()  
    ```  
  
4. Quando você não precisa representar, chame o <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> método para reverter a representação, conforme mostrado no código a seguir.  
  
    ```csharp  
    myImpersonation.Undo();  
    ```  
  
    ```vb  
    myImpersonation.Undo()  
    ```  
  
 Se confiável código já anexou um <xref:System.Security.Principal.WindowsPrincipal> do objeto para o thread, você pode chamar o método de instância **Impersonate**, que não utilize um token de conta. Observe que isso é útil somente quando o **WindowsPrincipal** objeto no thread representa um usuário diferente em que o processo está em execução atualmente. Por exemplo, você pode encontrar essa situação usando o ASP.NET com autenticação de Windows ativado e desativado de representação. Nesse caso, o processo está em execução em uma conta configurada em serviços de informações da Internet (IIS), enquanto a entidade atual representa o usuário do Windows que está acessando a página.  
  
 Observe que nem **Impersonate** nem **desfazer** alterações a **Principal** objeto (<xref:System.Security.Principal.IPrincipal>) associado com o contexto de chamada atual. Em vez disso, representação e alteração Revertendo o token associado com o processo de sistema operacional atual...  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Security.Principal.WindowsIdentity>
- <xref:System.Security.Principal.WindowsImpersonationContext>
- [Objetos Principal e Identity](../../../docs/standard/security/principal-and-identity-objects.md)
- [Interoperação com código não gerenciado](../../../docs/framework/interop/index.md)
