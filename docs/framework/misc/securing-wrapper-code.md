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
ms.openlocfilehash: ac278a4a3b06e0611e1cf57d079516a1dccf606b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397943"
---
# <a name="securing-wrapper-code"></a>Protegendo código de wrapper
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Código de wrapper, especialmente em que o wrapper possui confiança maior que o código que utiliza, pode abrir um conjunto exclusivo de vulnerabilidades de segurança. Qualquer coisa feita em nome de um chamador, onde as permissões limitadas do chamador não são incluídas na verificação de segurança apropriadas, é uma vulnerabilidade potencial para ser explorada.  
  
 Habilite nunca algo por meio de wrapper que o chamador não pôde fazer a mesmo. Este é um risco especial quando fazer algo que envolve uma verificação de segurança limitada, em vez de uma demanda de movimentação de pilha completos. Quando as verificações de nível único estão envolvidas, interposing o código de wrapper entre o chamador real e o elemento de API em questão pode facilmente fazer com que a verificação de segurança tenha êxito quando ele deve não e, portanto, diminuir a segurança.  
  
## <a name="delegates"></a>Delegados  
 Segurança de delegado difere entre as versões do .NET Framework.  Esta seção descreve os comportamentos diferentes delegado e associados considerações de segurança.  
  
### <a name="in-version-10-and-11-of-the-net-framework"></a>Na versão 1.0 e 1.1 do .NET Framework  
 Versão 1.0 e 1.1 do .NET Framework executar as seguintes ações de segurança contra um criador de delegate e um chamador de delegado.  
  
-   Quando um delegado é criado, as demandas de link de segurança sobre o método de destino de delegate são executadas em relação ao conjunto de concessão do criador de delegate.  Falha ao atender a ação de segurança resulta em um <xref:System.Security.SecurityException>.  
  
-   Quando o delegado é invocado, qualquer demandas de segurança existentes no chamador delegado são executadas.  
  
 Sempre que o seu código usa um <xref:System.Delegate> código menos confiável pode chamá-lo, certifique-se de que você não estiver habilitando o código menos confiável escalonar suas permissões. Se você levar um delegado e usá-lo posteriormente, o código que criou o delegado não está na pilha de chamadas e suas permissões não serão testadas se o código na ou sob o representante tenta uma operação protegida. Se seu código e o código chamador tem mais privilégios que o criador, o criador pode orquestrar o caminho da chamada sem fazer parte da pilha de chamadas.  
  
### <a name="in-version-20-and-later-versions-of-the-net-framework"></a>Na versão 2.0 e versões posteriores do .NET Framework  
 Diferentemente das versões anteriores, versão 2.0 e versões posteriores do .NET Framework executa ações de segurança contra o criador de delegate quando o representante é criado e chamado.  
  
-   Quando um delegado é criado, as demandas de link de segurança sobre o método de destino de delegate são executadas em relação ao conjunto de concessão do criador de delegate.  Falha ao atender a ação de segurança resulta em um <xref:System.Security.SecurityException>.  
  
-   O conjunto de concessões do criador de delegate também é capturado durante a criação de representante e armazenado com o delegado.  
  
-   Quando o delegado é invocado, do criador de delegate capturada concedido ao conjunto é avaliado primeiro contra qualquer demandas no contexto atual se o criador de delegate e o chamador pertencer aos assemblies diferentes.  Em seguida, são executadas de qualquer demandas de segurança existentes no chamador delegado.  
  
## <a name="link-demands-and-wrappers"></a>Demandas de link e wrappers  
 Um caso especial de proteção com demandas de link foi reforçado na infraestrutura de segurança, mas ainda é uma origem de possível ponto fraco em seu código.  
  
 Se o código totalmente confiável chamar uma propriedade, evento ou método protegido por um [LinkDemand](../../../docs/framework/misc/link-demands.md), a chamada terá êxito se o **LinkDemand** verificação de permissão para o chamador é atendida. Além disso, se o código totalmente confiável expõe uma classe que usa o nome de uma propriedade e chama seu **obter** acessador usando reflexão, que é chamada para o **obter** acessador terá êxito mesmo que o código de usuário faz não tem o direito de acessar essa propriedade. Isso ocorre porque o **LinkDemand** verifica somente o chamador imediato, que é o código totalmente confiável. Em essência, o código totalmente confiável está fazendo uma chamada privilegiada em nome do código do usuário sem certificando-se de que o código de usuário tem o direito de fazer essa chamada.  
  
 Para evitar tais falhas de segurança, o common language runtime estende a seleção em uma demanda de movimentação de pilha completa em qualquer chamada indireta para um método, construtor, propriedade ou evento protegidos por um **LinkDemand**. Essa proteção incorre em alguns custos de desempenho e altera a semântica da verificação de segurança; a solicitação de movimentação de pilha completa pode falhar em que a verificação rápida e um nível passaria.  
  
## <a name="assembly-loading-wrappers"></a>Wrappers de carregamento de assembly  
 Vários métodos usados para carregar o código gerenciado, incluindo <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, carregar assemblies com a evidência do chamador. Se você incluir qualquer um desses métodos, o sistema de segurança poderia usar concessão de permissão do seu código, em vez de permissões do chamador para o wrapper para carregar os assemblies. Você não deve permitir código menos confiável carregar um código que recebe as permissões mais altas que os do chamador para o wrapper.  
  
 Qualquer código que tenha confiança significativamente maior que um chamador potencial (incluindo um chamador de nível de permissões de Internet) ou confiança total pode diminuir o nível de segurança dessa maneira. Se seu código tem um método público que usa uma matriz de bytes e o transmite para **Load**e, portanto, criar um assembly em nome do chamador, ele pode interromper a segurança.  
  
 Esse problema se aplica aos seguintes elementos de API:  
  
-   <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
## <a name="demand-vs-linkdemand"></a>Demanda vs. LinkDemand  
 A segurança declarativa oferece dois tipos de verificações de segurança que são semelhantes, mas executam verificações muito diferentes. Você deve compreender as duas formas porque a opção errada pode resultar em perda de segurança ou desempenho fraca.  
  
 A segurança declarativa oferece as seguintes verificações de segurança:  
  
-   <xref:System.Security.Permissions.SecurityAction.Demand> Especifica a código acesso segurança na pilha. Todos os chamadores na pilha devem ter a permissão especificada ou a identidade para passar. **Demanda** ocorre em cada chamada porque a pilha pode conter chamadores diferentes. Se você chamar um método repetidamente, essa verificação de segurança ocorre a cada vez. **Demanda** é boa proteção contra ataques; código não autorizado tentar obter por meio dele será detectado.  
  
-   [LinkDemand](../../../docs/framework/misc/link-demands.md) ocorre em tempo de compilação just-in-time (JIT) e verifica somente o chamador imediato. Essa verificação de segurança não verifica o chamador do chamador. Depois de correspondência, não há nenhuma segurança adicional sobrecarga, independentemente de quantas vezes o chamador pode chamar. No entanto, também não há nenhuma proteção contra ataques de atração. Com **LinkDemand**, qualquer código que passe no teste e pode fazer referência a seu código pode comprometer a segurança, permitindo que o código mal-intencionado chamar usando o código não autorizado. Portanto, não use **LinkDemand** , a menos que todas as possíveis falhas podem ser completamente evitadas.  
  
    > [!NOTE]
    >  No [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], demandas de link foram substituídas pelo <xref:System.Security.SecurityCriticalAttribute> atributo <xref:System.Security.SecurityRuleSet.Level2> assemblies. O <xref:System.Security.SecurityCriticalAttribute> é equivalente a uma demanda de link de confiança total; no entanto, isso também afeta as regras de herança. Para obter mais informações sobre essa alteração, consulte [código transparente de segurança, nível 2](../../../docs/framework/misc/security-transparent-code-level-2.md).  
  
 As precauções extras necessárias ao usar **LinkDemand** deve ser programado individualmente; o sistema de segurança pode ajudar com a imposição. Qualquer erro abre uma vulnerabilidade de segurança. Todos os autorizados código que usa seu código deve ser responsável pela implementação de segurança adicional, fazendo o seguinte:  
  
-   Restringir o acesso do código de chamada para a classe ou assembly.  
  
-   Colocar a mesma segurança verifica o código de chamada que aparecem no código que está sendo chamado e obligating seus chamadores para fazer isso. Por exemplo, se você escrever código que chama um método que é protegida com uma **LinkDemand** para o <xref:System.Security.Permissions.SecurityPermission> com o <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> sinalizador especificado, o método também deve fazer uma **LinkDemand** (ou **Demanda**, que é mais seguro) para esta permissão. A exceção é se seu código usa o **LinkDemand**-método protegido de forma limitada que você decidir é seguro, considerando outros mecanismos de proteção de segurança (como demandas) no seu código. Nesse caso excepcional, o chamador assume a responsabilidade de diminuir a proteção de segurança no código subjacente.  
  
-   Garantir que chamadores do seu código não é possível instruir o seu código para chamar o código protegido em nome deles. Em outras palavras, os chamadores não podem forçar o código autorizado para passar parâmetros específicos para o código protegido, ou para obter os resultados de volta dele.  
  
### <a name="interfaces-and-link-demands"></a>Interfaces e demandas de Link  
 Se um método virtual, propriedade ou evento com **LinkDemand** substitui um método de classe base, o método da classe base também deve ter o mesmo **LinkDemand** para o método substituído para ser eficaz. É possível converter para o tipo de base e chame o método de classe base de código malicioso. Também Observe que as demandas de link pode ser adicionado implicitamente para assemblies que não têm o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo de nível de assembly.  
  
 É uma boa prática para proteger as implementações de método com demandas de link quando métodos de interface também tem demandas de link. Observe o seguinte sobre como usar as demandas de link com interfaces:  
  
-   Se você colocar um **LinkDemand** em um método público de uma classe que implementa um método de interface, o **LinkDemand** não serão aplicadas se você converter para a interface e chama o método. Nesse caso, pois vinculado em relação a interface, apenas o **LinkDemand** na interface é respeitada.  
  
 Revise os seguintes itens para problemas de segurança:  
  
-   Demandas de link explícita em métodos de interface. Verifique se essas demandas de link oferecem a proteção esperada. Determine se o código mal-intencionado pode usar uma conversão para contornar as demandas de link, conforme descrito anteriormente.  
  
-   Métodos virtuais com demandas de link aplicados.  
  
-   Tipos e as interfaces de implementação. Eles devem usar demandas de link consistentemente.  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)
