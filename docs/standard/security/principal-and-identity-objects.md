---
title: Objetos Principal e Identity
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- WindowsIdentity objects
- GenericIdentity objects
- GenericPrincipal objects
- identity objects, about identity objects
- security [.NET Framework], identity objects
- principal objects, about principal objects
- security [.NET Framework], principals
- WindowsPrincipal objects
ms.assetid: aa5930ad-f3d7-40aa-b6f6-c6edcd5c64f7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b8c7616a3187cd5fa28f231dffd15b0bfeea4b7f
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44080196"
---
# <a name="principal-and-identity-objects"></a>Objetos Principal e Identity
Código gerenciado pode descobrir a identidade ou a função de uma entidade de segurança por meio de um <xref:System.Security.Principal.IPrincipal> objeto que contém uma referência a um <xref:System.Security.Principal.IIdentity> objeto. Pode ser útil comparar objetos identity e principal para conceitos familiares, como contas de usuário e grupo. Na maioria dos ambientes de rede, as contas de usuário representam pessoas ou programas, enquanto as contas de grupo representam determinadas categorias de usuários e os direitos que eles possuem. Da mesma forma, os objetos de identidade do .NET Framework representam usuários, enquanto as funções representam as associações e contextos de segurança. No .NET Framework, o objeto de entidade encapsula um objeto de identidade e uma função. Aplicativos do .NET framework concedem direitos para a entidade de segurança com base em sua identidade ou, mais comumente, sua associação de função.  
  
## <a name="identity-objects"></a>Objetos de identidade  
 O objeto de identidade encapsula informações sobre o usuário ou entidade que está sendo validado. Em seu nível mais básico, os objetos de identidade contêm um nome e um tipo de autenticação. O nome pode ser um nome de usuário ou o nome de uma conta do Windows, enquanto o tipo de autenticação pode ser um protocolo de logon com suporte, como Kerberos V5, ou um valor personalizado. O .NET Framework define um <xref:System.Security.Principal.GenericIdentity> objeto que pode ser usado para a maioria dos cenários de logon personalizados e mais especializadas <xref:System.Security.Principal.WindowsIdentity> objeto que pode ser usado quando você deseja que seu aplicativo dependem da autenticação do Windows. Além disso, você pode definir sua própria classe de identidade que encapsula informações de usuário personalizada.  
  
 O <xref:System.Security.Principal.IIdentity> interface define propriedades para acessar um nome e um tipo de autenticação, como Kerberos V5 ou NTLM. Todos os **Identity** classes implementam a **IIdentity** interface. Não há nenhuma relação necessária entre um **identidade** token de objeto e o processo do Windows NT em que um thread está em execução atualmente. No entanto, se o **Identity** objeto é um **WindowsIdentity** do objeto, a identidade é presumida para representar um token de segurança do Windows NT.  
  
## <a name="principal-objects"></a>Objetos de entidade  
 O objeto de entidade representa o contexto de segurança sob a qual o código está em execução. Aplicativos que implementam a segurança baseada em função concedem direitos de acordo com a função associada a um objeto de entidade. Semelhante aos objetos de identidade, o .NET Framework fornece um <xref:System.Security.Principal.GenericPrincipal> objeto e um <xref:System.Security.Principal.WindowsPrincipal> objeto. Você também pode definir suas próprias classes de entidade de segurança personalizadas.  
  
 O <xref:System.Security.Principal.IPrincipal> interface define uma propriedade para acessar um associado **identidade** do objeto, bem como um método para determinar se o usuário identificado pela **Principal** objeto é um membro de um função determinada. Todos os **Principal** classes implementam a **IPrincipal** interface, bem como quaisquer propriedades e métodos adicionais que são necessários. Por exemplo, o common language runtime fornece a **WindowsPrincipal** classe, que implementa a funcionalidade adicional para o mapeamento de associação de grupo do Windows NT ou Windows 2000 para funções.  
  
 Um **Principal** objeto está associado a um contexto de chamada (<xref:System.Runtime.Remoting.Messaging.CallContext>) objeto dentro de um domínio de aplicativo (<xref:System.AppDomain>). Um contexto de chamada padrão sempre é criado com cada nova **AppDomain**, de modo que sempre está disponível para aceitar um contexto de chamada a **Principal** objeto. Quando um novo thread é criado, um **CallContext** objeto também é criado para o thread. O **Principal** referência de objeto é automaticamente copiada do thread de criação para o novo thread **CallContext**. Se o tempo de execução não pode determinar quais **Principal** objeto pertence ao criador do thread, ele segue a política padrão para **Principal** e **identidade** objeto criação.  
  
 Uma política específica de domínio de aplicativo configurável define as regras para decidir qual tipo de **Principal** objeto para associar um novo domínio de aplicativo. Quando a política de segurança permite, o tempo de execução pode criar **Principal** e **identidade** objetos que refletem o token do sistema operacional associado ao thread atual de execução. Por padrão, o tempo de execução usa **Principal** e **identidade** objetos que representam os usuários não autenticados. O tempo de execução não cria esses padrão **Principal** e **identidade** objetos até que o código tentar acessá-los.  
  
 Confiável o código que cria um domínio de aplicativo pode definir a política de domínio de aplicativo que controla a construção do padrão **Principal** e **identidade** objetos. Essa política específica de domínio de aplicativo se aplica a todos os threads de execução nesse domínio do aplicativo. Um host confiável e não gerenciado, inerentemente tem a capacidade de definir essa política, mas o código gerenciado que define essa política deve ter o <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> para controlar a diretiva de domínio.  
  
 Durante a transmissão de um **Principal** objeto entre domínios de aplicativo, mas dentro do mesmo processo (e, portanto, no mesmo computador), a infraestrutura de comunicação remota copia uma referência para o **Principal** objeto associado com o contexto do chamador ao contexto do computador chamado.  
  
## <a name="see-also"></a>Consulte também

- [Como criar um objeto WindowsPrincipal](../../../docs/standard/security/how-to-create-a-windowsprincipal-object.md)  
- [Como criar objetos GenericPrincipal e GenericIdentity](../../../docs/standard/security/how-to-create-genericprincipal-and-genericidentity-objects.md)  
- [Como substituir um objeto Principal](../../../docs/standard/security/replacing-a-principal-object.md)  
- [Representação e reversão](../../../docs/standard/security/impersonating-and-reverting.md)  
- [Segurança baseada em Função](../../../docs/standard/security/role-based-security.md)  
- [Principais conceitos de segurança](../../../docs/standard/security/key-security-concepts.md)
