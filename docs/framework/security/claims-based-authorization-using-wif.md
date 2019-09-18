---
title: Autorização baseada em declarações usando o WIF
ms.date: 03/30/2017
ms.assetid: e24000a3-8fd8-4c0e-bdf0-39882cc0f6d8
author: BrucePerlerMS
ms.openlocfilehash: ebf4c28bd2a46c21535b596af22d1fa420d20e71
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045498"
---
# <a name="claims-based-authorization-using-wif"></a>Autorização baseada em declarações usando o WIF
Em um aplicativo de terceira parte confiável, a autorização determina quais recursos uma identidade autenticada pode acessar e quais operações ela pode executar nesses recursos. A autorização inadequada ou fraca leva à divulgação de informações e à violação de dados. Este tópico descreve as abordagens disponíveis para implementar a autorização para aplicativos e serviços Web ASP.NET com reconhecimento de declarações usando o Windows Identity Foundation (WIF) e um Serviço de Token de Segurança (STS), por exemplo, o Serviço de Controle de Acesso (ACS) do Microsoft Azure.  
  
## <a name="overview"></a>Visão geral  
 Desde sua primeira versão, o .NET Framework oferece um mecanismo flexível para implementar a autorização. Esse mecanismo se baseia em duas interfaces simples – **IPrincipal** e **IIdentity**. As implementações concretas de **IIdentity** representam um usuário autenticado. Por exemplo, a implementação de **WindowsIdentity** representa um usuário que é autenticado pelo Active Directory e **GenericIdentity** representa um usuário cuja identidade é verificada por meio de um processo de autenticação personalizada. As implementações concretas de **IPrincipal** ajudam a verificar as permissões usando funções, dependendo do repositório de funções. Por exemplo, **WindowsPrincipal** verifica **WindowsIdentity** para obter a associação em grupos do Active Directory. Essa verificação é executada com uma chamada ao método **IsInRole** na interface **IPrincipal**. A verificação do acesso com base em funções é chamada de RBAC (Controle de Acesso Baseado em Função). Para obter mais informações, consulte [Controle de acesso baseado em função](claims-based-authorization-using-wif.md#BKMK_1).  As declarações podem ser usadas para transportar informações sobre funções para oferecer suporte a mecanismos de autorização com base em função.  
  
 As reivindicações também podem ser usadas para habilitar decisões de autorização mais complicadas, além de funções. As declarações podem ser baseada em praticamente todas as informações sobre o usuário – idade, CEP, tamanho de sapato, etc. Um mecanismo de controle de acesso baseado em declarações arbitrárias é chamado de autorização baseada em declarações. Para obter mais informações, consulte [Autorização baseada em declarações](claims-based-authorization-using-wif.md#BKMK_2).  
  
<a name="BKMK_1"></a>   
## <a name="role-based-access-control"></a>Controle de acesso baseado em funções  
 O RBAC é uma abordagem de autorização em que as permissões de usuário são gerenciadas e impostas por um aplicativo baseado em funções de usuário. Se um usuário tem a função necessária para executar uma ação, o acesso é concedido; caso contrário, o acesso é negado.  
  
### <a name="iprincipalisinrole-method"></a>Método IPrincipal.IsInRole  
 Para implementar a abordagem RBAC em aplicativos com reconhecimento de declaração, use o método **IsInRole ()** na interface **IPrincipal** , assim como você faria em aplicativos sem reconhecimento de declaração. Há várias maneiras de usar o método **IsInRole()** :  
  
- Chamando **IPrincipal.IsInRole("Administrator")** explicitamente. Nessa abordagem, o resultado é um booleano. Use-a em suas instruções condicionais. Ela pode ser usada arbitrariamente em qualquer local de seu código.  
  
- Usando a demanda de segurança **PrincipalPermission.Demand()** . Nessa abordagem, o resultado é uma exceção caso a demanda não seja atendida. Isso deve se ajustar à sua estratégia de tratamento de exceções. A geração de exceções é muito mais cara, de uma perspectiva de desempenho, comparada ao retorno do booliano. Isso pode ser usado em qualquer local de seu código.  
  
- Usando os atributos declarativos **[PrincipalPermission(SecurityAction.Demand, Role = "Administrator")]** . Essa abordagem é chamada declarativa porque é usada para decorar métodos. Ela não pode ser usada em blocos de códigos dentro das implementações do método. O resultado é uma exceção caso a demanda não seja atendida. Você deve se certificar de que ela se ajuste à sua estratégia de tratamento de exceções.  
  
- Usando a autorização de URL, usando a seção **\<authorization>** em **web.config**. Essa abordagem é apropriada quando você está gerenciando a autorização no nível de URL. Esse é o nível mais grosseiro entre os mencionados anteriormente. A vantagem dessa abordagem é que as alterações são feitas no arquivo de configuração, o que significa que o código não deve ser compilado para se beneficiar da alteração.  
  
### <a name="expressing-roles-as-claims"></a>Expressando funções como declarações  
 Quando o método **IsInRole()** é chamado, há uma verificação feita para ver se o usuário atual tem essa função. Em aplicativos com reconhecimento de declarações, a função é expressa por um tipo de declaração de função que deve estar disponível no token. O tipo de declaração de função é expresso usando o seguinte URI:  
  
 `http://schemas.microsoft.com/ws/2008/06/identity/claims/role`
  
 Há várias maneiras de enriquecer um token com um tipo de declaração de função:  
  
- **Durante a emissão de token**. Quando um usuário é autenticado, a declaração de função pode ser emitida pelo STS do provedor de identidade ou por um provedor de federação, como o ACS (Serviço de Controle de Acesso) do Microsoft Azure.  
  
- **Transformando declarações arbitrárias em um tipo de declaração de função usando ClaimsAuthenticationManager**. O ClaimsAuthenticationManager é um componente fornecido como parte do WIF. Ele permite que as solicitações sejam interceptadas quando iniciam um aplicativo, inspecionando os tokens e transformando-os adicionando, alterando ou removendo declarações. Para obter mais informações sobre como usar o ClaimsAuthenticationManager para transformar declarações, consulte [como: Implemente o RBAC (controle de acesso baseado em função) em um aplicativo ASP.NET com reconhecimento](https://go.microsoft.com/fwlink/?LinkID=247445)de declarações usando o WIF e o ACS.  
  
- **Mapeando declarações arbitrárias para um tipo de função usando a seção de configuração samlSecurityTokenRequirement** – uma abordagem declarativa em que a transformação de declarações é feita usando apenas a configuração, sem a necessidade de codificação.  
  
<a name="BKMK_2"></a>   
## <a name="claims-based-authorization"></a>Autorização baseada em declarações  
 A autorização baseada em declarações é uma abordagem em que a decisão de autorização para conceder ou negar acesso é baseada na lógica arbitrária que usa os dados disponíveis nas declarações para tomar a decisão. Lembre-se de que, no caso do RBAC, a única declaração usada foi a do tipo de função. Uma declaração de tipo de função foi usada para verificar se o usuário pertence à função específica ou não. Para ilustrar o processo de tomada de decisões de autorização usando a abordagem de autorização baseada em declarações, considere as seguintes etapas:  
  
1. O aplicativo recebe uma solicitação que exige que o usuário seja autenticado.  
  
2. O WIF redireciona o usuário ao seu provedor de identidade. Depois de autenticado, a solicitação do aplicativo é feita com um token de segurança associado representando o usuário que contém declarações sobre ele. O WIF associa essas declarações à entidade de segurança que representa o usuário.  
  
3. O aplicativo passa as declarações para o mecanismo de lógica de decisão. Ele pode ser um código na memória, uma chamada para um serviço Web, uma consulta em um banco de dados, um mecanismo sofisticado de regras, ou usando o ClaimsAuthorizationManager.  
  
4. O mecanismo de decisão calcula o resultado com base nas declarações.  
  
5. O acesso será concedido se o resultado for true, e negado se for false. Por exemplo, a regra pode ser que o usuário tenha 21 anos ou mais e more no estado de Washington.  
  
 O <xref:System.Security.Claims.ClaimsAuthorizationManager> é útil para exteriorizar a lógica de decisão para autorização baseada em declarações em seus aplicativos. O ClaimsAuthenticationManager é um componente do WIF que envia como parte do .NET 4.5. O ClaimsAuthorizationManager permite interceptar as solicitações recebidas e implementa as lógicas de sua escolha para tomar decisões de autorização com base nas declarações recebidas. Isso é importante quando a lógica de autorização precisa ser modificada. Nesse caso, usar o ClaimsAuthorizationManager não afetará a integridade do aplicativo, reduzindo a probabilidade de um erro do aplicativo em resultado da alteração. Para saber mais sobre como usar o ClaimsAuthorizationManager para implementar o controle de acesso baseado em declarações [, consulte Como: Implementar a autorização de declarações em um aplicativo ASP.NET com reconhecimento de declarações](https://go.microsoft.com/fwlink/?LinkID=247446)usando o WIF e o ACS.
