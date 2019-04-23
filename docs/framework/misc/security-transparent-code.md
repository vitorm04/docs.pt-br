---
title: Código transparente de segurança
ms.date: 03/30/2017
helpviewer_keywords:
- transparent code
- security-transparent code
ms.assetid: 4f3dd841-82f7-4659-aab0-6d2db2166c65
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5cb528bbb4f85cd4502b4e2efabbcf592ac6bd0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59974377"
---
# <a name="security-transparent-code"></a>Código transparente de segurança

<a name="top"></a>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

A segurança envolve três partes interativas: área restrita, permissões e imposição. Área restrita refere-se à prática de criar domínios isolados, onde algum código é tratado como totalmente confiável e outro código é restrito às permissões no conjunto de concessões para a área restrita. O código do aplicativo que é executado dentro do conjunto de concessões da área de segurança é considerado transparente; ou seja, ele não é possível executar todas as operações que podem afetar a segurança. O conjunto de concessões para a área restrita é determinada pela evidência (<xref:System.Security.Policy.Evidence> classe). A evidência identifica quais permissões específicas são necessárias para áreas restritas e quais tipos de áreas de segurança podem ser criados. Imposição se refere a permitir que código transparente seja executado somente em seu conjunto de concessões.

> [!IMPORTANT]
> Política de segurança era um elemento importante em versões anteriores do .NET Framework. Começando com o [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], política de segurança é obsoleta. A eliminação da política de segurança é separada da transparência de segurança. Para obter informações sobre os efeitos dessa alteração, consulte [compatibilidade de política de segurança de acesso do código e migração](../../../docs/framework/misc/code-access-security-policy-compatibility-and-migration.md).

Este tópico descreve o modelo de transparência em mais detalhes. Ele contém as seguintes seções:

- [Finalidade do modelo de transparência](#purpose)

- [Especificando o nível de transparência](#level)

- [Imposição de transparência](#enforcement)

<a name="purpose"></a>

## <a name="purpose-of-the-transparency-model"></a>Finalidade do Modelo de Transparência

A transparência é um mecanismo de imposição que separa o código que é executado como parte do aplicativo do código que é executado como parte da infra-estrutura. Transparência desenha uma barreira entre o código que pode fazer coisas privilegiadas (código crítico), como chamar código nativo e o código que não pode (código transparente). Código transparente pode executar comandos dentro dos limites do conjunto de permissões que ele está funcionando, mas não é possível executar, derivar de ou conter código crítico.

O principal objetivo da imposição de transparência é fornecer um mecanismo simples e eficiente para isolar grupos diferentes de código com base em privilégios. Dentro do contexto do modelo de área restrita, esses grupos de privilégio são totalmente confiáveis (isto é, não restritos) ou parcialmente confiáveis (isto é, restritos para o conjunto de permissões concedido à área restrita).

> [!IMPORTANT]
> O modelo de transparência transcende a segurança de acesso do código. Transparência é imposta pelo compilador just-in-time e permanece em efeito independentemente do conjunto de concessões para um assembly, incluindo confiança total.

Transparência foi introduzida no .NET versão 2.0 para simplificar o modelo de segurança e para torná-lo mais fácil escrever e implantar aplicativos e bibliotecas seguras. O código transparente também é usado no Microsoft Silverlight para simplificar o desenvolvimento de aplicativos parcialmente confiáveis.

> [!NOTE]
> Quando você desenvolve um aplicativo parcialmente confiável, você precisa estar ciente dos requisitos de permissão para seus hosts de destino. Você pode desenvolver um aplicativo que usa os recursos que não são permitidos por alguns hosts. Este aplicativo será compilado sem erros, mas falhará quando ele é carregado no ambiente hospedado. Se você tiver desenvolvido seu aplicativo usando o Visual Studio, você pode habilitar a depuração em confiança parcial ou em um conjunto do ambiente de desenvolvimento de permissões restritas. Para obter mais informações, confira [Como: Depurar um aplicativo ClickOnce com permissões restritas](/visualstudio/deployment/how-to-debug-a-clickonce-application-with-restricted-permissions). O recurso calcular permissões fornecido para aplicativos ClickOnce também está disponível para qualquer aplicativo parcialmente confiável.

[Voltar ao início](#top)

<a name="level"></a>

## <a name="specifying-the-transparency-level"></a>Especificando o Nível de Transparência

Nível de assembly <xref:System.Security.SecurityRulesAttribute> atributo seleciona explicitamente o <xref:System.Security.SecurityRuleSet> regras que o assembly seguirá. As regras são organizadas em um sistema de nível numérico, onde níveis superiores significam uma aplicação mais rigorosa de regras de segurança.

Os níveis são da seguinte maneira:

- Nível 2 (<xref:System.Security.SecurityRuleSet.Level2>) – a [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] regras de transparência.

- Nível 1 (<xref:System.Security.SecurityRuleSet.Level1>) – as regras de transparência do .NET Framework 2.0.

A principal diferença entre os dois níveis de transparência é que o nível 1 não impõe regras de transparência para chamadas de fora do assembly e destina-se somente para compatibilidade.

> [!IMPORTANT]
> Você deve especificar a transparência de nível 1 somente para compatibilidade; ou seja, especificar o nível 1 somente para o código que foi desenvolvido com o .NET Framework 3.5 ou anterior que usa o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> de atributo ou não usa o modelo de transparência. Por exemplo, use a transparência de nível 1 para assemblies do .NET Framework 2.0 que permitem chamadas de chamadores parcialmente confiáveis (APTCA). Para o código que é desenvolvido para o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], sempre use a transparência de nível 2.

### <a name="level-2-transparency"></a>Transparência de nível 2

Transparência de nível 2 foi introduzida no [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Os três tenets desse modelo são código transparente, código segurança-seguro-crítica e código de segurança crítica.

- Código transparente, independentemente das permissões que ele recebe (incluindo confiança total), pode chamar apenas outro código transparente ou código segurança-seguro-crítica. Se o código for parcialmente confiável, ele só pode executar ações permitidas pelo conjunto de permissões do domínio. O código transparente não pode fazer o seguinte:

  - Executar um <xref:System.Security.CodeAccessPermission.Assert%2A> operação ou elevação de privilégio.

  - Contém código não seguro ou não verificável.

  - Chame um código crítico diretamente.

  - Chamar código nativo ou código que tem o <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo.

  - Chamar um membro que é protegido por um <xref:System.Security.Permissions.SecurityAction.LinkDemand>.

  - Herda de tipos críticos.

    Além disso, os métodos transparentes não podem substituir métodos virtuais críticos ou implementar métodos críticos da interface.

- Código de segurança-seguro-crítica é totalmente confiável, mas pode ser chamado por código transparente. Ele expõe uma área da superfície limitada do código de confiança total. Verificações de exatidão e segurança ocorrem no código crítico.

- Código de segurança crítica pode chamar qualquer código e é totalmente confiável, mas ele não pode ser chamado pelo código transparent.

### <a name="level-1-transparency"></a>Transparência de Nível 1

O modelo de transparência de nível 1 foi introduzido no .NET Framework versão 2.0 para permitir que os desenvolvedores reduzir a quantidade de código que está sujeito a uma auditoria de segurança. Embora a transparência de nível 1 fosse publicamente disponível na versão 2.0, ela foi usada originalmente somente dentro da Microsoft para fins de auditoria de segurança. Por meio de anotações, os desenvolvedores são capazes de declarar quais tipos e membros podem executar elevações de segurança e outras ações confiáveis (de segurança crítica) e quais não podem (segurança-transparente). Código que é identificado como transparente não exige um alto grau de auditoria de segurança. Transparência de nível 1 indica que a imposição de transparência está limitada ao dentro do assembly. Em outras palavras, todos os tipos públicos ou membros que são identificados como crítico de segurança são essenciais de segurança somente dentro do assembly. Se você quiser impor segurança para esses tipos e membros quando eles são chamados de fora do assembly, você deve usar demandas de link para confiança total. Se você não fizer isso, membros e tipos de segurança crítica publicamente visíveis serão tratados como segurança-seguro-crítica e podem ser chamados pelo código parcialmente confiável fora do assembly.

O modelo de transparência de nível 1 tem as seguintes limitações:

- Tipos de segurança crítica e membros que são públicos são acessíveis de código transparente de segurança.

- As anotações de transparência são aplicadas somente dentro de um assembly.

- Tipos e membros críticos de segurança devem usar demandas de link para impor a segurança em chamadas fora do assembly.

- As regras de herança não são impostas.

- Existe a possibilidade de código transparente faça coisas prejudiciais quando executado em confiança total.

[Voltar ao início](#top)

<a name="enforcement"></a>

## <a name="transparency-enforcement"></a>Imposição de Transparência

Regras de transparência não são impostas até que a transparência é calculada. Nesse momento, um <xref:System.InvalidOperationException> será lançada se uma regra de transparência é violada. A hora em que a transparência é calculada depende de vários fatores e não pode ser prevista. Ele é calculado mais tarde. No [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], cálculo de transparência de nível de assembly ocorre mais cedo do que no .NET Framework 2.0. A única garantia é que o cálculo de transparência ocorrerá no momento em que ela é necessária. Isso é semelhante a como o compilador just-in-time (JIT) pode alterar o ponto quando um método é compilado e quaisquer erros nesse método são detectados. Cálculo de transparência é invisível se seu código não tem nenhum erro de transparência.

## <a name="see-also"></a>Consulte também

- [Código transparente de segurança, nível 1](../../../docs/framework/misc/security-transparent-code-level-1.md)
- [Código transparente de segurança, nível 2](../../../docs/framework/misc/security-transparent-code-level-2.md)
