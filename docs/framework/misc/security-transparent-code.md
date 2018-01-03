---
title: "Código transparente de segurança"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transparent code
- security-transparent code
ms.assetid: 4f3dd841-82f7-4659-aab0-6d2db2166c65
caps.latest.revision: "24"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 97db1cef60af267087e86f86ecd0a77021604642
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="security-transparent-code"></a>Código transparente de segurança
<a name="top"></a>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 A segurança envolve três partes interação: modo seguro, permissões e a imposição. Área restrita refere-se a prática de criar domínios isolados onde algum código é tratado como código totalmente confiável e outros é restrito às permissões na concessão definido para a área restrita. O código do aplicativo que é executado dentro do conjunto de concessão de área restrita é considerado para ser transparente; ou seja, ele não é possível executar todas as operações que podem afetar a segurança. A concessão definida para a área restrita é determinada pelo evidência (<xref:System.Security.Policy.Evidence> classe). Evidência identifica quais permissões específicas são necessárias por áreas restritas e quais tipos de caixas de podem ser criados. Imposição refere-se a permitir que o código transparente executar apenas dentro de seu conjunto de concessão.  
  
> [!IMPORTANT]
>  Política de segurança foi um elemento chave em versões anteriores do .NET Framework. Começando com o [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], política de segurança é obsoleta. A eliminação da política de segurança é separada da transparência de segurança. Para obter informações sobre os efeitos dessa alteração, consulte [compatibilidade de políticas de segurança de acesso do código e migração](../../../docs/framework/misc/code-access-security-policy-compatibility-and-migration.md).  
  
 Este tópico descreve o modelo de transparência em mais detalhes. Ele contém as seguintes seções:  
  
-   [Finalidade do modelo de transparência](#purpose)  
  
-   [Especificar o nível de transparência](#level)  
  
-   [Imposição de transparência](#enforcement)  
  
<a name="purpose"></a>   
## <a name="purpose-of-the-transparency-model"></a>Finalidade do Modelo de Transparência  
 Transparência é um mecanismo de imposição que separa o código que é executado como parte do aplicativo de código que é executado como parte da infraestrutura. Transparência desenha uma barreira entre o código que pode fazer coisas privilegiadas (código crítico), como chamar código nativo e o código que não é possível (código transparente). Código transparente pode executar comandos dentro dos limites do conjunto de permissões que ele esteja operando, mas não é possível executar, derivam ou conter código crítico.  
  
 O principal objetivo da imposição de transparência é fornecer um mecanismo simple e eficiente para isolar a diferentes grupos de código com base em privilégios. Dentro do contexto do modelo de modo seguro, esses grupos de privilégio são totalmente confiáveis (ou seja, não restritos,) ou parcialmente confiável (ou seja, restrita ao conjunto de permissões concedidas para a área restrita).  
  
> [!IMPORTANT]
>  O modelo de transparência transcende a segurança de acesso ao código. Transparência é imposta pelo compilador just-in-time e permanece em vigor, independentemente da concessão definido para um assembly, incluindo a confiança total.  
  
 Transparência foi introduzida o .NET Framework versão 2.0 para simplificar o modelo de segurança e para facilitar a gravação e implantar aplicativos e bibliotecas seguras. Código transparente também é usado no Microsoft Silverlight, para simplificar o desenvolvimento de aplicativos parcialmente confiáveis.  
  
> [!NOTE]
>  Quando você desenvolve um aplicativo parcialmente confiável, você precisa estar ciente dos requisitos de permissão para os hosts de destino. Você pode desenvolver um aplicativo que usa recursos que não são permitidos por alguns dos hosts. Este aplicativo será compilado sem erro, mas falhará quando ele é carregado no ambiente hospedado. Se você tiver desenvolvido seu aplicativo usando o Visual Studio, você pode habilitar a depuração em confiança parcial ou em uma permissão restrita definida no ambiente de desenvolvimento. Para obter mais informações, consulte [como: depurar um aplicativo ClickOnce com permissões restritas](/visualstudio/deployment/how-to-debug-a-clickonce-application-with-restricted-permissions). O recurso calcular permissões fornecido para aplicativos ClickOnce também está disponível para qualquer aplicativo parcialmente confiável.  
  
 [Voltar ao início](#top)  
  
<a name="level"></a>   
## <a name="specifying-the-transparency-level"></a>Especificando o Nível de Transparência  
 O nível de assembly <xref:System.Security.SecurityRulesAttribute> atributo explicitamente seleciona o <xref:System.Security.SecurityRuleSet> regras que segue o assembly. As regras são organizadas em um sistema de nível numérico, onde os níveis mais altos significam maior imposição de regras de segurança.  
  
 Os níveis são da seguinte maneira:  
  
-   Nível 2 (<xref:System.Security.SecurityRuleSet.Level2>) – o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] regras de transparência.  
  
-   Nível 1 (<xref:System.Security.SecurityRuleSet.Level1>) – as regras de transparência do .NET Framework 2.0.  
  
 A principal diferença entre os níveis de duas transparência é que o nível 1 não impõe regras de transparência para chamadas de fora do assembly e é destinado somente para compatibilidade.  
  
> [!IMPORTANT]
>  Você deve especificar a transparência de nível 1 somente para compatibilidade; ou seja, especificar o nível 1 somente para o código que foi desenvolvido com o .NET Framework 3.5 ou anterior que usa o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> de atributo ou não usar o modelo de transparência. Por exemplo, use a transparência de nível 1 para assemblies do .NET Framework 2.0 que permitem chamadas de chamadores parcialmente confiáveis (APTCA). Para o código desenvolvido para o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], sempre use a transparência de nível 2.  
  
### <a name="level-2-transparency"></a>Transparência de nível 2  
 Transparência de nível 2 foi introduzida no [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Os três princípios desse modelo são código transparente, código de segurança crítica segura e código crítico de segurança.  
  
-   Código transparente, independentemente das permissões que é concedido (incluindo a confiança total), pode chamar somente outros código transparente ou código de segurança crítica safe. Se o código é parcialmente confiável, ele só pode executar ações que são permitidas pelo conjunto de permissões do domínio. Código transparente não pode fazer o seguinte:  
  
    -   Executar um <xref:System.Security.CodeAccessPermission.Assert%2A> operação ou elevação de privilégio.  
  
    -   Contém o código não confiável ou.  
  
    -   Chame diretamente o código crítico.  
  
    -   Chamar código nativo ou em código que tem o <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo.  
  
    -   Chamar um membro que é protegido por um <xref:System.Security.Permissions.SecurityAction.LinkDemand>.  
  
    -   Herda de tipos críticos.  
  
     Além disso, os métodos transparentes não é possível substituir métodos virtuais críticos ou implementar métodos de interface crítico.  
  
-   Código de segurança crítica safe é totalmente confiável, mas pode ser chamado por código transparente. Ela expõe uma área da superfície limitada do código de confiança total. Verificações de integridade e segurança acontecem no código crítico para segurança.  
  
-   Código crítico de segurança pode chamar qualquer código e é totalmente confiável, mas ele não pode ser chamado por código transparente.  
  
### <a name="level-1-transparency"></a>Transparência de Nível 1  
 O modelo de transparência de nível 1 foi introduzido no .NET Framework versão 2.0 para permitir que os desenvolvedores reduzir a quantidade de código que está sujeito a uma auditoria de segurança. Embora a transparência de nível 1 publicamente disponível na versão 2.0, que foi usado principalmente apenas em Microsoft, para fins de auditoria de segurança. Por meio de anotações, os desenvolvedores são capazes de declarar os tipos e membros podem executar elevações de segurança e outras ações confiáveis (crítico de segurança) e que não é possível (transparência de segurança). Código que é identificado como transparente não exige um alto grau de auditoria de segurança. Transparência de nível 1 indica que a aplicação de transparência é limitada a dentro do assembly. Em outras palavras, qualquer tipos públicos ou membros que são identificados como críticas de segurança são críticas de segurança somente dentro do assembly. Se você deseja aplicar a segurança para esses tipos e membros quando eles são chamados de fora do assembly, você deve usar as demandas de link de confiança total. Se você não fizer isso, membros e tipos de segurança crítica publicamente visíveis são tratados como safe-crítico de segurança e podem ser chamados por código parcialmente confiável fora do assembly.  
  
 O modelo de transparência de nível 1 tem as seguintes limitações:  
  
-   Segurança crítica tipos e membros que são públicos são acessíveis no código transparente de segurança.  
  
-   As anotações de transparência são aplicadas apenas dentro de um assembly.  
  
-   Os membros e tipos críticos de segurança devem usar demandas de link para aplicar a segurança para chamadas de fora do assembly.  
  
-   Regras de herança não são impostas.  
  
-   Existe a possibilidade de código de transparência executar ações prejudiciais quando executado em confiança total.  
  
 [Voltar ao início](#top)  
  
<a name="enforcement"></a>   
## <a name="transparency-enforcement"></a>Imposição de Transparência  
 Regras de transparência não são impostas até transparência é calculada. Nesse momento, um <xref:System.InvalidOperationException> é gerada se uma regra de transparência é violada. O tempo de transparência é calculada depende de vários fatores e não pode ser previsto. Ele é calculado mais tarde. No [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], cálculo de transparência de nível de assembly ocorre com mais rapidez do que o .NET Framework 2.0. A garantia somente é que o cálculo de transparência ocorrerá no momento em que ela for necessária. Isso é semelhante a como o compilador just-in-time (JIT) pode alterar o ponto quando um método é compilado e quaisquer erros no método são detectados. Cálculo de transparência é invisível se seu código não tem erros de transparência.  
  
## <a name="see-also"></a>Consulte também  
 [Código transparente de segurança, nível 1](../../../docs/framework/misc/security-transparent-code-level-1.md)  
 [Código transparente de segurança, nível 2](../../../docs/framework/misc/security-transparent-code-level-2.md)
