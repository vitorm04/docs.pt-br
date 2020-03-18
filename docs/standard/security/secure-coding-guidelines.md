---
title: Diretrizes de codificação seguras para .NET
description: Design código para trabalhar com . Permissões impostas pela NET e outras aplicações para ajudar a impedir que o código malicioso acesse dados ou realize outras ações.
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
ms.openlocfilehash: 05f7e039ecdc0cd33baa015872924fb9e1f078aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187722"
---
# <a name="secure-coding-guidelines"></a>Diretrizes seguras de codificação

A segurança baseada em evidências e a segurança de acesso a códigos fornecem mecanismos muito poderosos e explícitos para implementar a segurança. A maioria do código de aplicativo pode simplesmente usar a infra-estrutura implementada pelo .NET. Em alguns casos, é necessária segurança específica do aplicativo adicional, construída por meio da ampliação do sistema de segurança ou usando novos métodos ad hoc.

Usando permissões impostas pelo .NET e outras aplicação em seu código, você deve erguer barreiras para impedir que o código malicioso acesse informações que você não deseja que ela tenha ou realize outras ações indesejáveis. Além disso, você deve encontrar um equilíbrio entre segurança e usabilidade em todos os cenários esperados usando código confiável.

Esta visão geral descreve as diferentes maneiras pelas quais o código pode ser projetado para trabalhar com o sistema de segurança.

## <a name="securing-resource-access"></a>Garantir o acesso a recursos

Ao projetar e escrever seu código, você precisa proteger e limitar o acesso que esse código tem aos recursos, especialmente ao usar ou invocar código de origem desconhecida. Portanto, tenha em mente as seguintes técnicas para garantir que seu código esteja seguro:

- Não use o Cas (Code Access Security).

- Não use código parcial de confiança.

- Não use o atributo [AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) (APTCA).

- Não use .NET Remoting.

- Não use DCOM (Distributed Component Object Model, modelo de objeto componente distribuído).

- Não use assuntos binários.

Segurança de acesso ao código e código transparente de segurança não são suportados como um limite de segurança com código parcialmente confiável. Não aconselhamos carregar e executar códigos de origens desconhecidas sem a adoção de medidas de segurança alternativas no local. As medidas alternativas de segurança são:

- Virtualização

- Contêineres de aplicativos

- Usuários e permissões do sistema operacional (OS)

- Contêineres do Hyper-V

## <a name="security-neutral-code"></a>Código neutro de segurança

Código neutro de segurança não faz nada explícito com o sistema de segurança. Funciona com todas as permissões que recebe. Embora aplicativos que não conseguem capturar exceções de segurança associadas a operações protegidas (como o uso de arquivos, redes e assim por diante) possam resultar em uma exceção não manuseada, o código neutro de segurança ainda tira proveito das tecnologias de segurança no .NET .

Uma biblioteca neutra em segurança tem características especiais que você deve entender. Suponha que sua biblioteca forneça elementos de API que usam arquivos ou chamam código não gerenciado. Se o seu código não tiver a permissão correspondente, ele não será executado como descrito. No entanto, mesmo que o código tenha a permissão, qualquer código de aplicativo que o chame deve ter a mesma permissão para funcionar. Se o código de chamada não tiver <xref:System.Security.SecurityException> a permissão certa, um aparecerá como resultado da caminhada da pilha de segurança de acesso ao código.

## <a name="application-code-that-isnt-a-reusable-component"></a>Código de aplicativo que não é um componente reutilizável

Se o seu código faz parte de um aplicativo que não será chamado por outro código, a segurança é simples e a codificação especial pode não ser necessária. No entanto, lembre-se que o código malicioso pode chamar seu código. Embora a segurança de acesso a código possa impedir que o código malicioso acesse recursos, esse código ainda pode ler valores de seus campos ou propriedades que possam conter informações confidenciais.

Além disso, se o seu código aceitar a entrada do usuário da Internet ou de outras fontes não confiáveis, você deve ter cuidado com a entrada maliciosa.

## <a name="managed-wrapper-to-native-code-implementation"></a>Invólucro gerenciado para implementação de código nativo

Normalmente, neste cenário, algumas funcionalidades úteis são implementadas em código nativo que você deseja disponibilizar para código gerenciado. Os invólucros gerenciados são fáceis de gravar usando invocação de plataforma ou interop COM. No entanto, se você fizer isso, os chamadores de seus invólucros devem ter direitos de código não gerenciados para ter sucesso. Na política padrão, isso significa que o código baixado de uma intranet ou a Internet não funcionará com os invólucros.

Em vez de dar direitos de código não gerenciados a todos os aplicativos que usam esses invólucros, é melhor dar esses direitos apenas ao código de invólucro. Se a funcionalidade subjacente não expor recursos e a implementação for igualmente segura, o invólucro só precisa fazer valer seus direitos, o que permite que qualquer código seja chamado através dele. Quando os recursos estão envolvidos, a codificação de segurança deve ser a mesma do caso de código de biblioteca descrito na próxima seção. Como o invólucro está potencialmente expondo os chamadores a esses recursos, a verificação cuidadosa da segurança do código nativo é necessária e é responsabilidade do invólucro.

## <a name="library-code-that-exposes-protected-resources"></a>Código da biblioteca que expõe recursos protegidos

A abordagem a seguir é a mais poderosa e, portanto, potencialmente perigosa (se feita incorretamente) para codificação de segurança: sua biblioteca serve como uma interface para outro código acessar certos recursos que não estão disponíveis de outra forma, assim como as classes .NET se aplicam permissões para os recursos que eles usam. Onde quer que você exponha um recurso, seu código deve primeiro exigir a permissão apropriada ao recurso (ou seja, ele deve realizar uma verificação de segurança) e, em seguida, normalmente, afirmar seus direitos para executar a operação real.

## <a name="related-topics"></a>Tópicos relacionados

|Title|Descrição|
|-----------|-----------------|
|[Protegendo dados de estado](securing-state-data.md)|Descreve como proteger membros privados.|
|[Segurança e entrada do usuário](security-and-user-input.md)|Descreve preocupações de segurança para aplicativos que aceitam a entrada do usuário.|
|[Segurança e condições de corrida](security-and-race-conditions.md)|Descreve como evitar condições de raça em seu código.|
|[Segurança e geração dinâmica de código](security-and-on-the-fly-code-generation.md)|Descreve preocupações de segurança para aplicativos que geram código dinâmico.|
|[Segurança baseada em papéis](role-based-security.md)|Descreve a segurança baseada em papéis .NET em detalhes e fornece instruções para usá-la em seu código.|
