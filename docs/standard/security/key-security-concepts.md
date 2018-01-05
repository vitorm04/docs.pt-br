---
title: "Conceitos principais de segurança"
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
- cpp
helpviewer_keywords:
- unauthorized access
- permissions [.NET Framework]
- security [.NET Framework], about security
ms.assetid: 3cfced4f-ea02-4e66-ae98-d69286363e98
caps.latest.revision: "22"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8e11e22d98954d9656357e11fbb4ca94ad673659
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="key-security-concepts"></a>Conceitos principais de segurança
O Microsoft .NET Framework oferece segurança baseada em função para ajudar a resolver problemas de segurança sobre código móvel e fornecer suporte que permite que os componentes para determinar quais usuários estão autorizados a fazer.  
  
## <a name="type-safety-and-security"></a>Segurança de tipos e segurança  
 Código fortemente tipado acessa somente os locais de memória que está autorizado a acessar. (Para esta discussão, segurança de tipo especificamente refere-se a segurança de tipo de memória e não deve ser confundida com segurança de tipo em um sentido mais amplo.) Por exemplo, código fortemente tipado não é possível ler valores de campos particulares de outro objeto. Ele acessa tipos somente em modos bem definidos, permitidos.  
  
 Durante a compilação do just-in-time (JIT), um processo de verificação opcional examina os metadados e a Microsoft intermediate language (MSIL) de um método a ser compilado por JIT no código de máquina nativo para verificar se eles estão tipo seguro. Esse processo será ignorado se o código tem permissão para ignorar a verificação. Para obter mais informações sobre a verificação, consulte [processo de execução gerenciado](../../../docs/standard/managed-execution-process.md).  
  
 Embora a verificação de segurança de tipo não é obrigatória para executar código gerenciado, a segurança de tipo desempenha um papel fundamental no isolamento de assembly e aplicação de segurança. Quando o código é do tipo seguro, o common language runtime pode isolar completamente assemblies uns dos outros. Esse isolamento ajuda a garantir que os assemblies não afetem entre si e aumenta a confiabilidade do aplicativo. Componentes de segurança de tipos podem executar com segurança no mesmo processo, mesmo se elas forem confiáveis em diferentes níveis. Quando o código não é um tipo de segurança, pode ocorrer efeitos colaterais indesejáveis. Por exemplo, o tempo de execução não pode impedir que o código gerenciado chamem o código nativo (não gerenciado) e executar operações mal-intencionadas. Quando o código é do tipo seguro, o mecanismo de imposição de segurança do tempo de execução garante que ele não acessar código nativo, a menos que ele tenha permissão para fazer isso. Todo o código que não é do tipo seguro deve ter sido concedido <xref:System.Security.Permissions.SecurityPermission> com o membro enum passado <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> para executar.  
  
 Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="principal"></a>Principal  
 Uma entidade de segurança representa a identidade e a função de um usuário e atua em nome do usuário. Segurança baseada em função no .NET Framework dá suporte a três tipos de entidades de segurança:  
  
-   Entidades de segurança genéricas representam usuários e funções que existem independentes de funções e usuários do Windows.  
  
-   Entidades de segurança do Windows que representam os usuários do Windows e suas funções (ou seus grupos do Windows). Uma entidade de segurança do Windows pode representar outro usuário, o que significa que a entidade de segurança pode acessar um recurso em um nome de usuário enquanto apresentando a identidade que pertence a esse usuário.  
  
-   Entidades de segurança personalizadas podem ser definidas por um aplicativo de qualquer forma que é necessário para esse aplicativo específico. Eles estendem a noção básica de funções e identidade do servidor principal.  
  
 Para obter mais informações, consulte [Principal e objetos de identidade](../../../docs/standard/security/principal-and-identity-objects.md).  
  
## <a name="authentication"></a>Autenticação  
 A autenticação é o processo de detecção e verificar a identidade de uma entidade de segurança examinando as credenciais do usuário e validar essas credenciais em alguma autoridade. As informações obtidas durante a autenticação serão diretamente utilizáveis por seu código. Você também pode usar a segurança baseada em função do .NET Framework para autenticar o usuário atual e para determinar se permitir que essa entidade de segurança acessar o seu código. Consulte as sobrecargas do <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> método para obter exemplos de como autenticar a entidade de segurança para funções específicas. Por exemplo, você pode usar o <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> sobrecarga para determinar se o usuário atual é um membro do grupo Administradores.  
  
 Uma variedade de mecanismos de autenticação são usados atualmente, muitos dos quais podem ser usados com segurança baseada em função do .NET Framework. Alguns dos mecanismos mais comumente usados são básicas, digest, Passport, o sistema operacional (como NTLM ou Kerberos) ou mecanismos definido pelo aplicativo.  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir exige que a entidade de segurança ativa seja um administrador. O `name` parâmetro é `null`, que permite que qualquer usuário que seja um administrador para passar a demanda.  
  
> [!NOTE]
>  No Windows Vista, o controle de conta de usuário (UAC) determina os privilégios de um usuário. Se for um membro do grupo Administradores Internos, você receberá dois tokens de acesso do tempo de execução: um token de acesso do usuário padrão e um token de acesso do administrador. Por padrão, você está na função de usuário padrão. Para executar o código que você deve ser um administrador, primeiro elevar seus privilégios de usuário padrão para o administrador. Você pode fazer isso quando você iniciar um aplicativo clicando duas vezes no ícone do aplicativo e que indica que você deseja executar como administrador.  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 O exemplo a seguir demonstra como determinar a identidade do principal e as funções disponíveis para a entidade de segurança. Um aplicativo deste exemplo pode ser para confirmar se o usuário atual está em uma função que você permite o uso de seu aplicativo.  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## <a name="authorization"></a>Autorização  
 A autorização é o processo de determinar se uma entidade tem permissão para executar uma ação solicitada. A autorização ocorre após a autenticação e usa as informações sobre as funções e a identidade da entidade de segurança para determinar quais recursos pode acessar a entidade de segurança. Você pode usar a segurança baseada em função do .NET Framework para implementar a autorização.
