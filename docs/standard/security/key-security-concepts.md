---
title: Conceitos principais de segurança
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- unauthorized access
- permissions [.NET Framework]
- security [.NET Framework], about security
ms.assetid: 3cfced4f-ea02-4e66-ae98-d69286363e98
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c483baeca9efcbc4a38020a7b2f4fa221a6b4028
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018613"
---
# <a name="key-security-concepts"></a>Conceitos principais de segurança
O Microsoft .NET Framework oferece segurança baseada em função para ajudar a resolver questões de segurança sobre o código móvel e fornecer suporte que permite que componentes de determinar quais usuários são autorizados a fazer.  
  
## <a name="type-safety-and-security"></a>Segurança de tipos e segurança  
 Código fortemente tipado acessa apenas os locais de memória que ele está autorizado a acessar. (Para esta discussão, segurança de tipos especificamente refere-se a segurança de tipo de memória e não deve ser confundida com o tipo de segurança em uma relação mais ampla.) Por exemplo, o código fortemente tipado não é possível ler valores de campos particulares de outro objeto. Acessa tipos somente de maneiras bem definidas e permitidas.  
  
 Durante a compilação do just-in-time (JIT), um processo de verificação opcional examina os metadados e Microsoft intermediate language (MSIL) de um método para ser compilado por JIT na linguagem nativa para verificar se eles são fortemente tipados. Esse processo será ignorado se o código tem permissão para ignorar a verificação. Para obter mais informações sobre a verificação, consulte [processo de execução gerenciada](../../../docs/standard/managed-execution-process.md).  
  
 Embora a verificação de segurança de tipo não é obrigatória para executar código gerenciado, a segurança de tipo desempenha um papel fundamental na imposição de segurança e isolamento do assembly. Quando o código é do tipo seguro, o common language runtime pode isolar assemblies uns dos outros completamente. Esse isolamento ajuda a garantir que os assemblies não podem se afetar negativamente e aumenta a confiabilidade do aplicativo. Os componentes fortemente tipados podem executar com segurança no mesmo processo, mesmo se elas forem confiáveis em níveis diferentes. Quando o código não é do tipo seguro, efeitos colaterais indesejados podem ocorrer. Por exemplo, o tempo de execução não pode impedir que o código gerenciado de chamar em código nativo (não gerenciado) e executar operações mal-intencionadas. Quando o código é do tipo seguro, o mecanismo de imposição de segurança do tempo de execução garante que ele acesse o código nativo, a menos que ele tem permissão para fazer isso. Todo o código que não é do tipo seguro deve ter sido concedido <xref:System.Security.Permissions.SecurityPermission> com o membro de enumeração passado <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> para ser executado.  
  
 Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="principal"></a>Principal  
 Uma entidade de segurança representa a identidade e a função de um usuário e atua em nome do usuário. Segurança baseada em função no .NET Framework dá suporte a três tipos de entidades de segurança:  
  
- As entidades de genéricas representam usuários e funções que existem independentemente das funções e usuários do Windows.  
  
- Entidades de segurança do Windows representam os usuários do Windows e suas funções (ou seus grupos do Windows). Uma entidade de segurança do Windows pode representar outro usuário, o que significa que a entidade de segurança pode acessar um recurso em um nome de usuário enquanto a apresentar a identidade que pertence a esse usuário.  
  
- As entidades personalizadas podem ser definidas por um aplicativo de qualquer forma que é necessário para esse aplicativo específico. Eles estendem a noção básica de identidade e a funções da entidade de segurança.  
  
 Para obter mais informações, consulte [Principal e objetos de identidade](../../../docs/standard/security/principal-and-identity-objects.md).  
  
## <a name="authentication"></a>Autenticação  
 A autenticação é o processo de detecção e verificar a identidade de uma entidade de segurança examinando as credenciais do usuário e validar essas credenciais em alguma autoridade. As informações obtidas durante a autenticação serão diretamente utilizáveis pelo seu código. Você também pode usar a segurança baseada em função do .NET Framework para autenticar o usuário atual e para determinar se deve permitir que essa entidade de segurança acessar o seu código. Consulte as sobrecargas do <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> método para obter exemplos de como autenticar a entidade de segurança para funções específicas. Por exemplo, você pode usar o <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> sobrecarga para determinar se o usuário atual é um membro do grupo Administradores.  
  
 Uma variedade de mecanismos de autenticação são usados hoje em dia, muitos dos quais podem ser usados com segurança baseada em função do .NET Framework. Alguns dos mecanismos mais comumente usados são básicas, digest, Passport, sistema operacional (como NTLM ou Kerberos) ou mecanismos de definido pelo aplicativo.  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir requer que a entidade de segurança do Active Directory seja um administrador. O `name` parâmetro é `null`, que permite que qualquer usuário que seja um administrador para passar a demanda.  
  
> [!NOTE]
>  No Windows Vista, o controle de conta de usuário (UAC) determina os privilégios de um usuário. Se for um membro do grupo Administradores Internos, você receberá dois tokens de acesso do tempo de execução: um token de acesso do usuário padrão e um token de acesso do administrador. Por padrão, você está na função de usuário padrão. Para executar o código que exige que você seja um administrador, você deve primeiro elevar seus privilégios de usuário padrão ao administrador. Você pode fazer isso quando você iniciar um aplicativo clicando duas vezes no ícone do aplicativo e que indica que você deseja executar como administrador.  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 O exemplo a seguir demonstra como determinar a identidade da entidade de segurança e as funções disponíveis para a entidade de segurança. Um aplicativo deste exemplo pode ser para confirmar se o usuário atual está em uma função que você permite o uso de seu aplicativo.  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## <a name="authorization"></a>Autorização  
 A autorização é o processo de determinar se uma entidade de segurança tem permissão para executar uma ação solicitada. A autorização ocorre após a autenticação e usa informações sobre as funções e a identidade da entidade de segurança para determinar quais recursos a entidade de segurança pode acessar. Você pode usar a segurança baseada em função do .NET Framework para implementar a autorização.
