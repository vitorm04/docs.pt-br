---
title: Protegendo código de wrapper
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], wrapper code
- wrapper code, securing
- secure coding, wrapper code
- code security, wrapper code
ms.assetid: 1df6c516-5bba-48bd-b450-1070e04b7389
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abbc817142ab6906a04b4dc053693f87109922dc
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487902"
---
# <a name="securing-wrapper-code"></a>Protegendo código de wrapper
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Código de wrapper, especialmente em que o wrapper tem confiança mais alto que o código que utiliza, pode abrir um conjunto exclusivo de vulnerabilidades de segurança. Qualquer coisa feita em nome de um chamador, em que as permissões do chamador limitadas não estão incluídas na verificação de segurança apropriadas, é um ponto fraco potencial para ser explorada.  
  
 Habilite nunca algo através do wrapper que o chamador não foi possível em si. Isso é um risco especial quando fazer algo que envolve uma verificação de segurança limitada, em vez de uma demanda de movimentação de pilha completa. Quando as verificações de nível único estão envolvidas, interposing o código de wrapper entre o chamador real e o elemento de API em questão pode facilmente fazer com que a verificação de segurança seja bem-sucedida quando ela deve não e, portanto, enfraquecer a segurança.  
  
## <a name="delegates"></a>Delegados  
 Segurança de delegado é diferente entre as versões do .NET Framework.  Esta seção descreve os comportamentos diferentes de delegado e associados a considerações de segurança.  
  
### <a name="in-version-10-and-11-of-the-net-framework"></a>Na versão 1.0 e 1.1 do .NET Framework  
 Versão 1.0 e 1.1 do .NET Framework execute as seguintes ações de segurança em relação a um criador de delegado e um chamador do delegado.  
  
- Quando um delegado é criado, as demandas de link de segurança no método de destino de delegado são executadas em conjunto de concessões do criador do delegado.  Falha para satisfazer a ação de segurança resulta em um <xref:System.Security.SecurityException>.  
  
- Quando o delegado é invocado, qualquer demandas de segurança existentes no chamador delegado são executadas.  
  
 Sempre que seu código recebe um <xref:System.Delegate> do código menos confiável que possa chamá-lo, certifique-se de que você não estiver habilitando o código menos confiável escalonar suas permissões. Se você levar um delegado e usá-lo posteriormente, o código que criou o delegado não está na pilha de chamadas e suas permissões não serão testadas se o código no ou sob o delegado tentar uma operação de protegido. Se seu código e o código chamador tem mais privilégios que o criador, o criador pode orquestrar o caminho da chamada sem fazer parte da pilha de chamadas.  
  
### <a name="in-version-20-and-later-versions-of-the-net-framework"></a>Na versão 2.0 e versões posteriores do .NET Framework  
 Diferentemente das versões anteriores, versão 2.0 e versões posteriores do .NET Framework executa a ação de segurança contra o criador de delegado quando o delegado é criado e chamado.  
  
- Quando um delegado é criado, as demandas de link de segurança no método de destino de delegado são executadas em conjunto de concessões do criador do delegado.  Falha para satisfazer a ação de segurança resulta em um <xref:System.Security.SecurityException>.  
  
- Conjunto de concessões do criador de delegado também é capturado durante a criação de delegado e armazenado com o delegado.  
  
- Quando o delegado é invocado, conjunto de concessões capturados de delegado do criador primeiro é avaliado em relação a qualquer demandas no contexto atual se o criador de delegado e o chamador pertencerem a assemblies diferentes.  Em seguida, qualquer demandas de segurança existentes no chamador delegado são executadas.  
  
## <a name="link-demands-and-wrappers"></a>Demandas de link e wrappers  
 Um caso especial de proteção com demandas de link foi reforçado na infra-estrutura de segurança, mas ainda é uma fonte de um possível ponto fraco em seu código.  
  
 Se o código totalmente confiável chamar uma propriedade, evento ou método protegido por um [LinkDemand](../../../docs/framework/misc/link-demands.md), a chamada terá êxito se o **LinkDemand** verificação de permissão para que o chamador é atendida. Além disso, se o código totalmente confiável expõe uma classe que usa o nome de uma propriedade e chamadas de seu **Obtenha** acessador usando a reflexão, que é chamada para o **obter** acessador for bem-sucedida, mesmo que o código de usuário faz não tem o direito de acessar essa propriedade. Isso ocorre porque o **LinkDemand** verifica somente o chamador imediato, que é o código totalmente confiável. Em essência, o código totalmente confiável está fazendo uma chamada de privilegiadas em nome do código do usuário sem certificando-se de que o código de usuário tem o direito de fazer essa chamada.  
  
 Para evitar tais falhas de segurança, o common language runtime estende a seleção em uma demanda de movimentação de pilha completa em qualquer chamada indireta para um método, construtor, propriedade ou evento protegido por um **LinkDemand**. Essa proteção incorre em alguns custos de desempenho e altera a semântica da verificação de segurança; a demanda de movimentação de pilha completo poderá falhar em que a verificação de um nível mais rápida passaria.  
  
## <a name="assembly-loading-wrappers"></a>Wrappers de carregamento de assembly  
 Vários métodos usados para carregar o código gerenciado, incluindo <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, carregar assemblies com a evidência do chamador. Se você encapsula qualquer um desses métodos, o sistema de segurança pode usar concessão de permissão do seu código, em vez de permissões do chamador para o wrapper, carregar os assemblies. Você não deve permitir que código menos confiável carregar o código que recebeu permissões mais elevadas que as do chamador para o wrapper.  
  
 Qualquer código que tenha confiança significativamente maior do que um chamador potencial (incluindo um chamador de nível de permissões da Internet) ou confiança total pode diminuir o nível de segurança dessa maneira. Se o código tem um método público que pega uma matriz de bytes e a passa **Load**e, portanto, criando um assembly em nome do chamador, ele poderá interromper a segurança.  
  
 Esse problema se aplica aos seguintes elementos de API:  
  
- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
## <a name="demand-vs-linkdemand"></a>Demanda vs. LinkDemand  
 Segurança declarativa oferece dois tipos de verificações de segurança que são semelhantes, mas executam verificações muito diferentes. Você deve compreender as duas formas porque a escolha errada pode resultar em perda de segurança ou o desempenho fraca.  
  
 Segurança declarativa oferece as seguintes verificações de segurança:  
  
- <xref:System.Security.Permissions.SecurityAction.Demand> Especifica a movimentação de pilha de segurança de acesso de código. Todos os chamadores na pilha devem ter a permissão especificada ou a identidade para passar. **Demanda** ocorre em todas as chamadas, porque a pilha talvez contenha chamadores diferentes. Se você chamar um método repetidamente, essa verificação de segurança ocorre cada vez. **Demanda** é boa proteção contra ataques de atração código não autorizado tentar obter por meio dele será detectado.  
  
- [LinkDemand](../../../docs/framework/misc/link-demands.md) ocorre em tempo de compilação just-in-time (JIT) e verifica somente o chamador imediato. Essa verificação de segurança não verifica chamador o chamador do. Depois que essa verificação passa, não há nenhuma segurança adicional sobrecarga, independentemente de quantas vezes o chamador pode chamar. No entanto, também não há nenhuma proteção contra ataques de atração. Com o **LinkDemand**, qualquer código que é aprovado no teste e pode fazer referência a seu código pode potencialmente quebrar a segurança, permitindo que o código mal-intencionado chamar usando o código não autorizado. Portanto, não use **LinkDemand** , a menos que todas as falhas possíveis podem ser completamente evitadas.  
  
    > [!NOTE]
    >  No .NET Framework 4, as demandas de link foram substituídas pela <xref:System.Security.SecurityCriticalAttribute> de atributo em <xref:System.Security.SecurityRuleSet.Level2> assemblies. O <xref:System.Security.SecurityCriticalAttribute> é equivalente a uma demanda de link para confiança total; no entanto, isso também afeta as regras de herança. Para obter mais informações sobre essa alteração, consulte [código transparente de segurança, nível 2](../../../docs/framework/misc/security-transparent-code-level-2.md).  
  
 As precauções extras necessárias ao utilizar **LinkDemand** deve ser programado individualmente; o sistema de segurança pode ajudar com a imposição. Qualquer erro abre uma vulnerabilidade de segurança. Todos os autorizados código que usa seu código deve ser responsável por implementar segurança adicional fazendo o seguinte:  
  
- Restringindo o acesso do código de chamada da classe ou assembly.  
  
- Colocando a mesma segurança verifica no código de chamada que aparecem no código que está sendo chamado e obligating seus chamadores para fazê-lo. Por exemplo, se você escrever código que chama um método que é protegido com uma **LinkDemand** para o <xref:System.Security.Permissions.SecurityPermission> com o <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> sinalizador for especificado, o método também deve fazer uma **LinkDemand** (ou **Demanda**, que é mais forte) para essa permissão. A exceção é se o seu código usa o **LinkDemand**-método protegido de forma limitada que você achar que é seguro, considerando outros mecanismos de proteção de segurança (como demandas) em seu código. Nesse caso excepcional, o chamador assume a responsabilidade em enfraquecer a proteção de segurança no código subjacente.  
  
- Garantir que os chamadores do seu código não é possível induzir seu código chama o código protegido em nome deles. Em outras palavras, os chamadores não podem forçar o código não autorizado para passar parâmetros específicos para o código protegido ou para obter resultados dela.  
  
### <a name="interfaces-and-link-demands"></a>Interfaces e demandas de Link  
 Se um método virtual, propriedade ou evento com **LinkDemand** substitui um método de classe base, o método de classe base também deve ter o mesmo **LinkDemand** para o método substituído para serem eficazes. É possível a conversão de volta ao tipo base e chame o método de classe base por código mal-intencionado. Também Observe que as demandas de link pode ser adicionado implicitamente a assemblies que não têm o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo de nível de assembly.  
  
 É uma boa prática para proteger as implementações de método com demandas de link quando métodos de interface também tem demandas de link. Observe o seguinte sobre como usar demandas de link com interfaces:  
  
- Se você colocar uma **LinkDemand** em um método público de uma classe que implementa um método de interface, o **LinkDemand** não serão impostas se, em seguida, convertido para a interface e chamar o método. Nesse caso, porque você vinculou com base na interface, apenas o **LinkDemand** na interface será respeitada.  
  
 Examine os seguintes itens para problemas de segurança:  
  
- Demandas de link explícito em métodos de interface. Verifique se essas demandas de link oferecem a proteção esperada. Determine se o código mal-intencionado pode usar uma conversão para contornar as demandas de link, conforme descrito anteriormente.  
  
- Métodos virtuais com demandas de link aplicados.  
  
- Tipos e as interfaces que elas implementam. Eles devem usar demandas de link consistentemente.  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)
