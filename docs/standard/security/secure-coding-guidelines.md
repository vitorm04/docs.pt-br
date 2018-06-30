---
title: Diretrizes de codificação segura para .NET
ms.date: 06/28/2018
helpviewer_keywords:
- managed wrapper to native code implementation
- secure coding
- reusable components
- library code that exposes protected resources
- code, security
- code security
- secure coding, options
- components [.NET], security
- code security, options
- security-neutral code
- security [.NET], coding guidelines
ms.assetid: 4f882d94-262b-4494-b0a6-ba9ba1f5f177
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b3a8f0dfc1a2b5e09722876b73281ed1d8b6334e
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106730"
---
# <a name="secure-coding-guidelines"></a>Diretrizes de codificação segura

Segurança de acesso do código e segurança baseada em evidência fornecem mecanismos muito poderosos, explícitos para implementar a segurança. A maioria dos códigos de aplicativo podem simplesmente usar a infraestrutura implementada pelo .NET. Em alguns casos, adicionais de segurança específicas do aplicativo é necessária, criado, estendendo o sistema de segurança ou usando novos métodos ad hoc.

Usando o .NET aplicadas permissões e outra imposição em seu código, você deve colocar as barreiras para impedir que o código mal-intencionado acessem informações que você não quê-la tenha ou executar outras ações indesejáveis. Além disso, você deve obter um equilíbrio entre segurança e facilidade de uso em todos os cenários esperados usando código confiável.

Esta visão geral descreve as diferentes maneiras de código pode ser projetado para trabalhar com o sistema de segurança.

## <a name="securing-resource-access"></a>Protegendo o acesso aos recursos

Ao criar e gravar seu código, você precisa proteger e limitar o acesso ao código tem a recursos, especialmente ao usar ou chamar o código de origem desconhecida. Portanto, tenha em mente as seguintes técnicas para garantir que seu código é seguro:

- Não use a segurança de acesso do código (CAS).

- Não use o código de confiança parcial.

- Não use o [AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) atributo (APTCA).

- Não use a comunicação remota do .NET.

- Não use o modelo de objeto componente distribuído (DCOM).

- Não use formatadores binários.

Não há suporte para segurança de acesso do código e o código transparente de segurança como um limite de segurança com código parcialmente confiável. Não aconselhamos carregar e executar códigos de origens desconhecidas sem a adoção de medidas de segurança alternativas no local. As medidas de segurança alternativa são:

- Virtualização

- AppContainers

- Permissões e os usuários do sistema operacional (SO)

- Contêineres do Hyper-V

## <a name="security-neutral-code"></a>Código de segurança neutra

Código de segurança neutra não faz nada explícita com o sistema de segurança. Seja executada com as permissões que ele recebe. Embora os aplicativos que falham ao capturar exceções de segurança associadas com operações protegidas (como o uso de arquivos, rede e assim por diante) podem resultar em uma exceção sem tratamento, o código de segurança neutra ainda se beneficia das tecnologias de segurança no .NET .

Uma biblioteca de segurança neutra tem características especiais que você deve entender. Suponha que sua biblioteca fornece elementos de API que usam arquivos ou chamam código não gerenciado. Se seu código não tiver a permissão correspondente, ele não será executado como descrito. No entanto, mesmo que o código tenha a permissão, qualquer código de aplicativo que faz a chamada deve ter a mesma permissão para trabalhar. Se o código de chamada não tiver permissão, um <xref:System.Security.SecurityException> aparece como resultado a código acesso segurança na pilha.

## <a name="application-code-that-isnt-a-reusable-component"></a>Código do aplicativo que não é um componente reutilizável

Se seu código é parte de um aplicativo que não seja chamado por outro código, a segurança é simple e codificação especial pode não ser necessário. No entanto, lembre-se de que o código mal-intencionado pode chamar seu código. Enquanto a segurança de acesso ao código pode parar mal-intencionados acessem os recursos, esse código ainda pode ler os valores de seus campos ou propriedades que podem conter informações confidenciais.

Além disso, se seu código aceita entrada do usuário da Internet ou outras fontes não confiáveis, você deve ser cuidadoso com entrada mal-intencionada.

## <a name="managed-wrapper-to-native-code-implementation"></a>Gerenciado wrapper para a implementação de código nativo

Normalmente neste cenário, algumas funcionalidades úteis é implementada no código nativo que você deseja disponibilizar para código gerenciado. Wrappers gerenciados são fáceis de gravação usando qualquer uma das plataformas invoke ou interoperabilidade COM. No entanto, se você fizer isso, os chamadores do seu wrappers devem ter direitos de código não gerenciado para ter êxito. Política padrão, isso significa que o código obtido por uma intranet ou Internet não funcionará com os wrappers.

Em vez de conceder direitos de código não gerenciado para todos os aplicativos que usam esses wrappers, é melhor conceder esses direitos somente para o código de wrapper. Se a funcionalidade subjacente expõe sem recursos e a implementação da mesma forma é segura, o wrapper só precisa declarar seus direitos, que permite que qualquer código chamar por meio dele. Quando os recursos estão envolvidos, codificação de segurança deve ser o mesmo que o caso de código de biblioteca descrito na próxima seção. Porque o wrapper está potencialmente expondo chamadores a esses recursos, cuidadosa verificação de segurança de código nativo é necessária e é responsabilidade do wrapper.

## <a name="library-code-that-exposes-protected-resources"></a>Código da biblioteca que expõe recursos protegidos

A abordagem a seguir é mais eficiente e, portanto, potencialmente perigosa (se tiver feito incorretamente) para a codificação de segurança: sua biblioteca serve como uma interface para outro código acessar certos recursos que não disponíveis, caso contrário, assim como impõem as classes do .NET permissões para os recursos que eles usam. Sempre que você expõe um recurso, seu código primeiro deve exigem a permissão apropriada para o recurso (ou seja, ele deve executar uma verificação de segurança) e, em seguida, normalmente assert seus direitos para executar a operação real.

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Proteção de dados de estado](securing-state-data.md)|Descreve como proteger membros particulares.|
|[Segurança e entrada do usuário](security-and-user-input.md)|Descreve as questões de segurança para aplicativos que aceitam entrada do usuário.|
|[Segurança e condições de corrida](security-and-race-conditions.md)|Descreve como evitar condições de corrida em seu código.|
|[Segurança e geração dinâmica de código](security-and-on-the-fly-code-generation.md)|Descreve as questões de segurança para aplicativos que geram código dinâmico.|
|[Segurança baseada em Função](role-based-security.md)|Descreve a segurança baseada em função do .NET em detalhes e fornece instruções para usá-lo em seu código.|
