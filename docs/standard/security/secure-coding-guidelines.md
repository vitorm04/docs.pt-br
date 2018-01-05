---
title: "Diretrizes de codificação segura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed wrapper to native code implementation
- secure coding
- reusable components
- library code that exposes protected resources
- code, security
- code security
- secure coding, options
- components [.NET Framework], security
- code security, options
- security-neutral code
- security [.NET Framework], coding guidelines
ms.assetid: 4f882d94-262b-4494-b0a6-ba9ba1f5f177
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3e75f3c74c5966ce5ce22b23f7ba179e903d37aa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="secure-coding-guidelines"></a>Diretrizes de codificação segura
Segurança de acesso do código e segurança baseada em evidência fornecem mecanismos muito poderosos, explícitos para implementar a segurança. A maioria dos códigos de aplicativo podem simplesmente usar a infraestrutura implementada pelo .NET Framework. Em alguns casos, adicionais de segurança específicas do aplicativo é necessária, criado, estendendo o sistema de segurança ou usando novos métodos ad hoc.  
  
 Usando as permissões aplicadas pelo .NET Framework e outra imposição em seu código, você deve colocar as barreiras para impedir que um código mal-intencionado de obtenção de informações que você não quê-la tenha ou executar outras ações indesejáveis. Além disso, você deve obter um equilíbrio entre segurança e facilidade de uso em todos os cenários esperados usando código confiável.  
  
 Esta visão geral descreve as diferentes maneiras de código pode ser projetado para trabalhar com o sistema de segurança.  
  
## <a name="securing-resource-access"></a>Protegendo o acesso aos recursos  
 Ao criar e gravar seu código, você precisa proteger e limitar o acesso ao código tem a recursos, especialmente ao usar ou chamar o código de origem desconhecida. Portanto, tenha em mente as seguintes técnicas para garantir que seu código é seguro:  
  
-   Não use a segurança de acesso do código (CAS).  
  
-   Não use o código de confiança parcial.  
  
-   Não use a comunicação remota do .NET.  
  
-   Não use o modelo de objeto componente distribuído (DCOM).  
  
-   Não use formatadores binários.  
  
 Segurança de acesso do código e o código transparente de segurança não terão suporte como um limite de segurança com código parcialmente confiável. Não aconselhamos carregar e executar códigos de origens desconhecidas sem a adoção de medidas de segurança alternativas no local. As medidas de segurança alternativa são:  
  
-   Virtualização  
  
-   AppContainers  
  
-   Permissões e os usuários do sistema operacional (SO)  
  
-   Contêineres do Hyper-V  
  
## <a name="security-neutral-code"></a>Código de segurança neutra  
 Código de segurança neutra não faz nada explícita com o sistema de segurança. Seja executada com as permissões que ele recebe. Embora os aplicativos que falham ao capturar exceções de segurança associadas com operações protegidas (como o uso de arquivos, rede e assim por diante) podem resultar em uma exceção sem tratamento, o código de segurança neutra ainda tira proveito da segurança do .NET Framework tecnologias.  
  
 Uma biblioteca de segurança neutra tem características especiais que você deve entender. Suponha que sua biblioteca fornece elementos de API que usam arquivos ou chamam código não gerenciado; Se seu código não tem a permissão correspondente, ele não será executado como descrito. No entanto, mesmo que o código tenha a permissão, qualquer código de aplicativo que faz a chamada deve ter a mesma permissão para trabalhar. Se o código de chamada não tiver permissão, um <xref:System.Security.SecurityException> aparece como resultado a código acesso segurança na pilha.  
  
## <a name="application-code-that-is-not-a-reusable-component"></a>Código do aplicativo que não é um componente reutilizável  
 Se seu código é parte de um aplicativo que não será chamado por outro código, a segurança é simple e codificação especial pode não ser necessário. No entanto, lembre-se de que o código mal-intencionado pode chamar seu código. Enquanto a segurança de acesso ao código pode parar mal-intencionados acessem os recursos, esse código ainda pode ler os valores de seus campos ou propriedades que podem conter informações confidenciais.  
  
 Além disso, se seu código aceita entrada do usuário da Internet ou outras fontes não confiáveis, você deve ser cuidadoso com entrada mal-intencionada.  
  
## <a name="managed-wrapper-to-native-code-implementation"></a>Gerenciado Wrapper para a implementação de código nativo  
 Normalmente neste cenário, algumas funcionalidades úteis é implementada no código nativo que você deseja disponibilizar para código gerenciado. Wrappers gerenciados são fáceis de gravação usando qualquer uma das plataformas invoke ou interoperabilidade COM. No entanto, se você fizer isso, os chamadores do seu wrappers devem ter direitos de código não gerenciado para ter êxito. Política padrão, isso significa que o código obtido por uma intranet ou Internet não funcionará com os wrappers.  
  
 Em vez de apresentar todos os aplicativos que usam esses direitos de código não gerenciado wrappers, é melhor conceder esses direitos somente para o código de wrapper. Se a funcionalidade subjacente expõe sem recursos e a implementação da mesma forma é segura, o wrapper só precisa declarar seus direitos, que permite que qualquer código chamar por meio dele. Quando os recursos estão envolvidos, codificação de segurança deve ser o mesmo que o caso de código de biblioteca descrito na próxima seção. Porque o wrapper está potencialmente expondo chamadores a esses recursos, cuidadosa verificação de segurança de código nativo é necessária e é responsabilidade do wrapper.  
  
## <a name="library-code-that-exposes-protected-resources"></a>Código da biblioteca que expõe recursos protegidos  
 Isso é mais eficiente e, portanto, potencialmente perigoso (se tiver feito incorretamente) abordagem para codificação de segurança: sua biblioteca serve como uma interface para outro código acessar certos recursos que não estão disponíveis, assim como as classes do .NET Framework aplicar permissões para os recursos que eles usam. Sempre que você expõe um recurso, seu código primeiro deve exigem a permissão apropriada para o recurso (ou seja, ele deve executar uma verificação de segurança) e, em seguida, normalmente assert seus direitos para executar a operação real.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Proteção de dados de estado](../../../docs/standard/security/securing-state-data.md)|Descreve como proteger membros particulares.|  
|[Segurança e entrada do usuário](../../../docs/standard/security/security-and-user-input.md)|Descreve as questões de segurança para aplicativos que aceitam entrada do usuário.|  
|[Segurança e condições de corrida](../../../docs/standard/security/security-and-race-conditions.md)|Descreve como evitar condições de corrida em seu código.|  
|[Segurança e geração dinâmica de código](../../../docs/standard/security/security-and-on-the-fly-code-generation.md)|Descreve as questões de segurança para aplicativos que geram código dinâmico.|  
|[Segurança baseada em Função](../../../docs/standard/security/role-based-security.md)|Descreve a segurança baseada em função do .NET Framework em detalhes e fornece instruções para usá-lo em seu código.|
