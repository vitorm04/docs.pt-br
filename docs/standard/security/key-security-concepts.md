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
ms.openlocfilehash: b7bcb7e56ca14d129eadcaeac19452d4a443713d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400655"
---
# <a name="key-security-concepts"></a>Conceitos principais de segurança
O Microsoft .NET Framework oferece segurança baseada em papéis para ajudar a resolver preocupações de segurança sobre o código móvel e para fornecer suporte que permite que os componentes determinem o que os usuários estão autorizados a fazer.  
  
## <a name="type-safety-and-security"></a>Tipo segurança e segurança  
 O código de segurança de tipo acessa apenas os locais de memória que está autorizado a acessar. (Para esta discussão, a segurança do tipo refere-se especificamente à segurança do tipo de memória e não deve ser confundida com a segurança do tipo em um aspecto mais amplo.) Por exemplo, o código de segurança de tipo não pode ler valores de campos privados de outro objeto. Ele acessa tipos apenas de maneiras bem definidas e permitidas.  
  
 Durante a compilação just-in-time (JIT), um processo opcional de verificação examina os metadados e a linguagem intermediária da Microsoft (MSIL) de um método a ser compilado pelo JIT em código de máquina nativa para verificar se eles são seguros para o tipo. Este processo é ignorado se o código tiver permissão para contornar a verificação. Para obter mais informações sobre verificação, consulte [Processo de Execução Gerenciado](../../../docs/standard/managed-execution-process.md).  
  
 Embora a verificação da segurança do tipo não seja obrigatória para executar código gerenciado, a segurança do tipo desempenha um papel crucial no isolamento da montagem e na aplicação da segurança. Quando o código é seguro para o tipo, o tempo de execução da linguagem comum pode isolar completamente os conjuntos uns dos outros. Esse isolamento ajuda a garantir que os conjuntos não possam afetar negativamente uns aos outros e aumenta a confiabilidade do aplicativo. Os componentes de segurança de tipo podem ser executados com segurança no mesmo processo, mesmo que sejam confiáveis em diferentes níveis. Quando o código não é seguro, efeitos colaterais indesejados podem ocorrer. Por exemplo, o tempo de execução não pode impedir que o código gerenciado seja chamado para código nativo (não gerenciado) e realize operações maliciosas. Quando o código é seguro para o tipo, o mecanismo de aplicação de segurança do runtime garante que ele não acesse o código nativo a menos que tenha permissão para fazê-lo. Todo o código que não é <xref:System.Security.Permissions.SecurityPermission> seguro do tipo <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> deve ter sido concedido com o membro enum aprovado para executar.  
  
 Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="principal"></a>Principal  
 Um diretor representa a identidade e o papel de um usuário e atua em nome do usuário. A segurança baseada em função no .NET Framework suporta três tipos de princípios:  
  
- Os princípios genéricos representam usuários e funções que existem independentes dos usuários e funções do Windows.  
  
- Os diretores do Windows representam os usuários do Windows e suas funções (ou seus grupos do Windows). Um diretor do Windows pode se passar por outro usuário, o que significa que o principal pode acessar um recurso em nome de um usuário enquanto apresenta a identidade que pertence a esse usuário.  
  
- Os princípios personalizados podem ser definidos por um aplicativo de qualquer maneira necessária para esse aplicativo em particular. Eles podem estender a noção básica da identidade e dos papéis do diretor.  
  
 Para obter mais informações, consulte [Principal e Objetos de Identidade](../../../docs/standard/security/principal-and-identity-objects.md).  
  
## <a name="authentication"></a>Autenticação  
 Autenticação é o processo de descobrir e verificar a identidade de um diretor examinando as credenciais do usuário e validando essas credenciais contra alguma autoridade. As informações obtidas durante a autenticação são diretamente utilizáveis pelo seu código. Você também pode usar o segurança baseado em função .NET Framework para autenticar o usuário atual e determinar se permite que esse principal acesse seu código. Veja as sobrecargas <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> do método para exemplos de como autenticar o principal para funções específicas. Por exemplo, você <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> pode usar a sobrecarga para determinar se o usuário atual é um membro do grupo Administradores.  
  
 Uma variedade de mecanismos de autenticação são usados hoje, muitos dos quais podem ser usados com segurança baseada em função .NET Framework. Alguns dos mecanismos mais usados são básicos, digest, Passport, sistema operacional (como NTLM ou Kerberos), ou mecanismos definidos por aplicativos.  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir exige que o principal ativo seja um administrador. O `name` parâmetro `null`é , que permite que qualquer usuário que é um administrador passe a demanda.  
  
> [!NOTE]
> No Windows Vista, o User Account Control (UAC) determina os privilégios de um usuário. Se for um membro do grupo Administradores Internos, você receberá dois tokens de acesso do tempo de execução: um token de acesso do usuário padrão e um token de acesso do administrador. Por padrão, você está na função de usuário padrão. Para executar o código que exige que você seja um administrador, você deve primeiro elevar seus privilégios de usuário padrão para administrador. Você pode fazer isso ao iniciar um aplicativo clicando com o botão direito do mouse no ícone do aplicativo e indicando que deseja executar como administrador.  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 O exemplo a seguir demonstra como determinar a identidade do diretor e as funções disponíveis para o diretor. Um aplicativo deste exemplo pode ser para confirmar que o usuário atual está em uma função que você permite usar seu aplicativo.  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## <a name="authorization"></a>Autorização  
 Autorização é o processo de determinar se um diretor pode realizar uma ação solicitada. A autorização ocorre após a autenticação e usa informações sobre a identidade e funções do diretor para determinar quais recursos o principal pode acessar. Você pode usar o segurança baseado em função .NET Framework para implementar a autorização.
