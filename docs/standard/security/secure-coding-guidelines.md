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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018639"
---
# <a name="secure-coding-guidelines"></a>Diretrizes de codificação segura

Segurança baseada em evidência e segurança de acesso do código fornecem mecanismos muito poderosos, explícitos para implementar a segurança. A maioria dos códigos de aplicativo pode simplesmente usar a infra-estrutura implementada pelo .NET. Em alguns casos, os adicionais de segurança específicos do aplicativo é necessária, compilada estendendo o sistema de segurança ou usando novos métodos ad hoc.

Usando o .NET imposta permissões e outra imposição em seu código, você deve colocar as barreiras para impedir que códigos mal-intencionados de acessar informações que você não deseja que ela tenha ou executar outras ações indesejáveis. Além disso, você deve obter um equilíbrio entre segurança e usabilidade em todos os cenários esperados usando código confiável.

Esta visão geral descreve as diferentes maneiras de código pode ser projetado para trabalhar com o sistema de segurança.

## <a name="securing-resource-access"></a>Protegendo o acesso aos recursos

Ao projetar e escrever seu código, você precisa proteger e limitar o acesso que o código tem a recursos, especialmente ao usar ou chamar o código de origem desconhecida. Portanto, tenha em mente as seguintes técnicas para garantir que o código está seguro:

- Não use a segurança de acesso do código (CAS).

- Não use o código de confiança parcial.

- Não use o [AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) atributo (APTCA).

- Não use a comunicação remota do .NET.

- Não use o modelo de objeto componente distribuído (DCOM).

- Não use formatadores binários.

Não há suporte para segurança de acesso do código e o código transparente de segurança como um limite de segurança com código parcialmente confiável. Não aconselhamos carregar e executar códigos de origens desconhecidas sem a adoção de medidas de segurança alternativas no local. As medidas de segurança alternativas são:

- Virtualização

- AppContainers

- Permissões e os usuários do sistema operacional (SO)

- Contêineres do Hyper-V

## <a name="security-neutral-code"></a>Código de segurança neutra

Código de segurança neutra não faz nada explícito com o sistema de segurança. Ele é executado com quaisquer permissões que ele recebe. Embora os aplicativos que falham ao capturar exceções de segurança associadas a operações protegidas (como o uso de arquivos, rede e assim por diante) podem resultar em uma exceção sem tratamento, o código neutro de segurança ainda aproveita as tecnologias de segurança no .NET .

Uma biblioteca de segurança neutra tem características especiais que você deve compreender. Suponha que sua biblioteca fornece os elementos de API que usam arquivos ou chamam código não gerenciado. Se seu código não tiver a permissão correspondente, ele não será executado conforme descrito. No entanto, mesmo que o código tenha a permissão, qualquer código de aplicativo que faz a chamada deve ter a mesma permissão para trabalhar. Se o código de chamada não tem a permissão correta, uma <xref:System.Security.SecurityException> aparece como resultado a movimentação de pilha de segurança de acesso de código.

## <a name="application-code-that-isnt-a-reusable-component"></a>Código do aplicativo que não é um componente reutilizável

Se seu código fizer parte de um aplicativo que não será chamado por outro código, a segurança é simple e codificação especial pode não ser necessário. No entanto, lembre-se de que o código mal-intencionado pode chamar seu código. Enquanto a segurança de acesso do código poderá parar de códigos mal-intencionados de acessar os recursos, tal código ainda pode ler os valores de seus campos ou propriedades que podem conter informações confidenciais.

Além disso, se seu código aceita entrada do usuário da Internet ou de outras fontes não confiáveis, você deve ser cuidadoso com entrada mal-intencionada.

## <a name="managed-wrapper-to-native-code-implementation"></a>Gerenciado wrapper para a implementação de código nativo

Normalmente nesse cenário, algumas funcionalidades úteis é implementada em código nativo que você deseja disponibilizar para código gerenciado. Invólucros gerenciados são fáceis de gravação usando invocação de qualquer plataforma ou a interoperabilidade COM. No entanto, se você fizer isso, os chamadores de sua wrappers devem ter direitos de código não gerenciado para ser bem-sucedido. Sob a política padrão, isso significa que o código baixado de uma intranet ou Internet não funcionará com os wrappers.

Em vez de conceder direitos de código não gerenciado para todos os aplicativos que usam esses wrappers, é melhor fornecer esses direitos somente para o código de wrapper. Se a funcionalidade subjacente não expõe nenhum recurso e a implementação é segura da mesma forma, o wrapper só precisa declarar seus direitos, que permite que qualquer código chame por meio dele. Quando os recursos estão envolvidos, codificação de segurança deve ser o mesmo que o caso de código da biblioteca descrito na próxima seção. Porque o wrapper está potencialmente expondo os chamadores a esses recursos, verificação de cuidado do que a segurança do código nativo é necessária e é responsabilidade do wrapper.

## <a name="library-code-that-exposes-protected-resources"></a>Recursos do código da biblioteca que expõe protegidos

A abordagem a seguir é mais poderosa e, portanto, potencialmente perigosa (caso seja realizado incorretamente) para a codificação de segurança: sua biblioteca serve como uma interface para outro código para acessar determinados recursos que não disponíveis, caso contrário, assim como impõem as classes do .NET permissões para os recursos que eles usam. Sempre que você exponha um recurso, seu código deve exigir primeiro a permissão apropriada para o recurso (ou seja, ele deve executar uma verificação de segurança) e, em seguida, normalmente, declarar seus direitos para executar a operação real.

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Proteção de dados de estado](securing-state-data.md)|Descreve como proteger os membros privados.|
|[Segurança e entrada do usuário](security-and-user-input.md)|Descreve problemas de segurança para aplicativos que aceitam a entrada do usuário.|
|[Segurança e condições de corrida](security-and-race-conditions.md)|Descreve como evitar condições de corrida em seu código.|
|[Segurança e geração dinâmica de código](security-and-on-the-fly-code-generation.md)|Descreve problemas de segurança para aplicativos que geram código dinâmico.|
|[Segurança baseada em Função](role-based-security.md)|Descreve a segurança baseada em função do .NET em detalhes e fornece instruções sobre como usá-lo em seu código.|
