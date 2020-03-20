---
title: Protegendo código de wrapper
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], wrapper code
- wrapper code, securing
- secure coding, wrapper code
- code security, wrapper code
ms.assetid: 1df6c516-5bba-48bd-b450-1070e04b7389
ms.openlocfilehash: 3d38a4d4fd33798cf5987f5ce67305725ad9daec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399906"
---
# <a name="securing-wrapper-code"></a>Protegendo código de wrapper
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 O código do invólucro, especialmente quando o invólucro tem maior confiança do que o código que o usa, pode abrir um conjunto único de fraquezas de segurança. Qualquer coisa feita em nome de um chamador, onde as permissões limitadas do chamador não estão incluídas na verificação de segurança apropriada, é uma fraqueza potencial a ser explorada.  
  
 Nunca habilite algo através do invólucro que o chamador não poderia fazer sozinho. Este é um perigo especial ao fazer algo que envolve uma verificação de segurança limitada, em oposição a uma demanda de caminhada de pilha completa. Quando as verificações de nível único estão envolvidas, interpor o código de invólucro entre o chamador real e o elemento API em questão pode facilmente fazer com que a verificação de segurança tenha sucesso quando não deveria, enfraquecendo assim a segurança.  
  
## <a name="delegates"></a>Delega  
 A segurança do delegado difere entre as versões do Quadro .NET.  Esta seção descreve os diferentes comportamentos dos delegados e considerações de segurança associadas.  
  
### <a name="in-version-10-and-11-of-the-net-framework"></a>Na versão 1.0 e 1.1 do Quadro .NET  
 As versões 1.0 e 1.1 do .NET Framework executam as seguintes ações de segurança contra um criador de delegados e um chamador de delegado.  
  
- Quando um delegado é criado, as demandas de link de segurança no método de destino do delegado são realizadas contra o conjunto de subvenções do delegado criador.  A falha em satisfazer a <xref:System.Security.SecurityException>ação de segurança resulta em um .  
  
- Quando o delegado é invocado, quaisquer exigências de segurança existentes sobre o chamador do delegado são realizadas.  
  
 Sempre que seu <xref:System.Delegate> código pegar um código menos confiável que possa chamá-lo, certifique-se de que você não está permitindo que o código menos confiável aumente suas permissões. Se você pegar um delegado e usá-lo mais tarde, o código que criou o delegado não está na pilha de chamadas e suas permissões não serão testadas se o código dentro ou o delegado tentar uma operação protegida. Se seu código e o código de chamada tiverem privilégios maiores que o criador, o criador pode orquestrar o caminho de chamada sem fazer parte da pilha de chamadas.  
  
### <a name="in-version-20-and-later-versions-of-the-net-framework"></a>Na versão 2.0 e versões posteriores do Quadro .NET  
 Ao contrário das versões anteriores, a versão 2.0 e versões posteriores do .NET Framework executa ações de segurança contra o criador do delegado quando o delegado é criado e chamado.  
  
- Quando um delegado é criado, as demandas de link de segurança no método de destino do delegado são realizadas contra o conjunto de subvenções do delegado criador.  A falha em satisfazer a <xref:System.Security.SecurityException>ação de segurança resulta em um .  
  
- O conjunto de subvenções do delegado também é capturado durante a criação do delegado e armazenado com o delegado.  
  
- Quando o delegado é invocado, o conjunto de subvenções capturado sustais do delegado é primeiro avaliado contra quaisquer demandas no contexto atual se o criador e o chamador do delegado pertencerem a assembléias diferentes.  Em seguida, todas as exigências de segurança existentes no chamador do delegado são executadas.  
  
## <a name="link-demands-and-wrappers"></a>Demandas de links e invólucros  
 Um caso de proteção especial com demandas de links foi reforçado na infra-estrutura de segurança, mas ainda é uma fonte de possível fraqueza em seu código.  
  
 Se o código totalmente confiável chamar uma propriedade, evento ou método protegido por um [LinkDemand,](link-demands.md)a chamada será bem-sucedida se a verificação de permissão **LinkDemand** para o chamador estiver satisfeita. Além disso, se o código totalmente confiável expõe uma classe que leva o nome de uma propriedade e chama seu acessório **get** usando reflexão, essa chamada para o acessório **get** é bem sucedida mesmo que o código do usuário não tenha o direito de acessar essa propriedade. Isso porque o **LinkDemand** verifica apenas o chamador imediato, que é o código totalmente confiável. Em essência, o código totalmente confiável é fazer uma chamada privilegiada em nome do código do usuário sem ter certeza de que o código do usuário tem o direito de fazer essa chamada.  
  
 Para ajudar a evitar tais falhas de segurança, o tempo de execução do idioma comum estende a verificação para uma demanda completa de empilhadeiras em qualquer chamada indireta para um método, construtor, propriedade ou evento protegido por um **LinkDemand**. Essa proteção incorre em alguns custos de desempenho e altera a semântica da verificação de segurança; a demanda completa de stack-walk pode falhar onde a verificação mais rápida e de um nível teria passado.  
  
## <a name="assembly-loading-wrappers"></a>Embalagem de carregamento de montagem  
 Vários métodos usados para carregar <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>código gerenciado, incluindo , conjuntos de carga com a evidência do chamador. Se você envolver qualquer um desses métodos, o sistema de segurança poderia usar a concessão de permissão do seu código, em vez das permissões do chamador para o seu invólucro, para carregar os conjuntos. Você não deve permitir que códigos menos confiáveis carreguem códigos que recebem permissões mais altas do que as do chamador para o seu invólucro.  
  
 Qualquer código que tenha total confiança ou confiança significativamente maior do que um chamador em potencial (incluindo um chamador de nível de permissões da Internet) poderia enfraquecer a segurança desta forma. Se o seu código tiver um método público que pegue uma matriz de bytes e passe-o para **Assembly.Load,** criando assim uma montagem em nome do chamador, ele pode quebrar a segurança.  
  
 Este problema se aplica aos seguintes elementos da API:  
  
- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
## <a name="demand-vs-linkdemand"></a>Demand versus LinkDemand  
 A segurança declarativa oferece dois tipos de verificações de segurança que são semelhantes, mas realizam verificações muito diferentes. Você deve entender ambas as formas porque a escolha errada pode resultar em baixa segurança ou perda de desempenho.  
  
 A segurança declarativa oferece as seguintes verificações de segurança:  
  
- <xref:System.Security.Permissions.SecurityAction.Demand>especifica a caminhada da pilha de segurança de acesso ao código. Todos os chamadores na pilha devem ter a permissão ou identidade especificadas para passar. **A demanda** ocorre em cada chamada porque a pilha pode conter diferentes chamadores. Se você chamar um método repetidamente, esta verificação de segurança ocorre todas as vezes. **A demanda** é uma boa proteção contra ataques de atração; código não autorizado tentando passar por ele será detectado.  
  
- [LinkDemand](link-demands.md) acontece no tempo de compilação just-in-time (JIT) e verifica apenas o chamador imediato. Esta verificação de segurança não verifica o chamador do chamador. Uma vez que esta verificação passa, não há sobrecarga adicional de segurança, não importa quantas vezes o chamador possa ligar. No entanto, também não há proteção contra ataques de atração. Com **o LinkDemand**, qualquer código que passe no teste e possa fazer referência ao seu código pode potencialmente quebrar a segurança, permitindo que o código malicioso ligue usando o código autorizado. Portanto, não use **LinkDemand** a menos que todas as possíveis fraquezas possam ser completamente evitadas.  
  
    > [!NOTE]
    > No Quadro .NET 4, as demandas de <xref:System.Security.SecurityCriticalAttribute> link <xref:System.Security.SecurityRuleSet.Level2> foram substituídas pelo atributo em assembléias. O <xref:System.Security.SecurityCriticalAttribute> equivalente a uma demanda de link para confiança total; no entanto, também afeta as regras de herança. Para obter mais informações sobre essa alteração, consulte [Código transparente de segurança, nível 2](security-transparent-code-level-2.md).  
  
 As precauções extras necessárias ao usar **o LinkDemand** devem ser programadas individualmente; o sistema de segurança pode ajudar na aplicação. Qualquer erro abre uma fraqueza de segurança. Todo o código autorizado que usa seu código deve ser responsável pela implementação de segurança adicional, fazendo o seguinte:  
  
- Restringindo o acesso do código de chamada à classe ou à montagem.  
  
- Colocando as mesmas verificações de segurança no código de chamada que aparecem no código que está sendo chamado e obrigando seus chamadores a fazê-lo. Por exemplo, se você escrever código que chama um método <xref:System.Security.Permissions.SecurityPermission> protegido <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> com um **LinkDemand** para o com o sinalizador especificado, seu método também deve fazer um **LinkDemand** (ou **Demand**, que é mais forte) para essa permissão. A exceção é se o seu código usar o método protegido pelo **LinkDemand**de forma limitada que você decidir que é seguro, dado outros mecanismos de proteção de segurança (como demandas) em seu código. Neste caso excepcional, o chamador assume a responsabilidade de enfraquecer a proteção de segurança no código subjacente.  
  
- Garantir que os chamadores do seu código não possam enganar seu código para chamar o código protegido em seu nome. Em outras palavras, os chamadores não podem forçar o código autorizado a passar parâmetros específicos para o código protegido ou obter resultados de volta a partir dele.  
  
### <a name="interfaces-and-link-demands"></a>Interfaces e Demandas de Link  
 Se um método virtual, propriedade ou evento com **LinkDemand** substitui um método de classe base, o método de classe base também deve ter o mesmo **LinkDemand** para o método substituído para ser eficaz. É possível que o código malicioso volte ao tipo base e chame o método de classe base. Observe também que as demandas de link podem ser <xref:System.Security.AllowPartiallyTrustedCallersAttribute> adicionadas implicitamente a assembléias que não têm o atributo de nível de montagem.  
  
 É uma boa prática proteger implementações de métodos com demandas de link quando os métodos de interface também têm demandas de link. Observe o seguinte sobre o uso de demandas de link com interfaces:  
  
- Se você colocar um **LinkDemand** em um método público de uma classe que implemente um método de interface, o **LinkDemand** não será aplicado se você for lançado para a interface e chamar o método. Neste caso, como você se vinculou à interface, apenas o **LinkDemand** na interface é honrado.  
  
 Revise os seguintes itens para problemas de segurança:  
  
- Demandas explícitas de link em métodos de interface. Certifique-se de que essas demandas de links ofereçam a proteção esperada. Determine se o código malicioso pode usar um elenco para contornar as demandas de link descritas anteriormente.  
  
- Métodos virtuais com demandas de link aplicadas.  
  
- Tipos e interfaces que implementam. Estes devem usar demandas de link de forma consistente.  
  
## <a name="see-also"></a>Confira também

- [Diretrizes de codificação segura](../../standard/security/secure-coding-guidelines.md)
