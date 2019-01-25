---
title: Diretrizes de codificação segura para código não gerenciado
ms.date: 03/30/2017
helpviewer_keywords:
- code security, unmanaged code
- unmanaged code, securing
- security [.NET Framework], unmanaged code
- secure coding, unmanaged code
ms.assetid: a8d15139-d368-4c9c-a747-ba757781117c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf9071f8b5c4569ace53b13f7b9b7282bf8e87c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711967"
---
# <a name="secure-coding-guidelines-for-unmanaged-code"></a>Diretrizes de codificação segura para código não gerenciado
Um código de biblioteca precisa chamar o código não gerenciado (por exemplo, APIs de código nativo, assim como Win32). Visto que isso significa que sair do perímetro de segurança para código gerenciado, o devido cuidado é necessário. Se seu código é neutro em termos de segurança, seu código e qualquer outro código que o chama devem ter permissão de código não gerenciado (<xref:System.Security.Permissions.SecurityPermission> com o sinalizador <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> especificado).  
  
 No entanto, geralmente não é razoável para o chamador ter permissões tão elevadas. Nesses casos, seu código confiável pode ser intermediário, semelhante ao wrapper gerenciado ou código da biblioteca descrito em [Protegendo código de Wrapper](../../../docs/framework/misc/securing-wrapper-code.md). Se a funcionalidade de código não gerenciado subjacente for totalmente segura, ele poderá ser exposto diretamente; caso contrário, uma verificação de permissão adequada (demanda) será necessária primeiro.  
  
 Quando seu código chama código não gerenciado, mas você não deseja exigir que os chamadores tenham permissão para acessar código não gerenciado, você deve declarar esse direito. Uma declaração bloqueia a movimentação da pilha em seu quadro. Você deve ter cuidado para não criar uma falha de segurança nesse processo. Geralmente, isso significa que você deve exigir uma permissão adequada dos chamadores e usar código não gerenciado para executar apenas o que ela permite e nada mais. Em alguns casos (por exemplo, em uma função de obtenção de hora do dia), o código não gerenciado pode ser diretamente exposto a chamadores sem nenhuma verificação de segurança. Em qualquer caso, qualquer código que fizer uma declaração deverá assumir a responsabilidade pela segurança.  
  
 Já que qualquer código gerenciado que fornece um caminho de código para código nativo é um destino potencial para código mal-intencionado, determinar qual código não gerenciado pode ser usado com segurança e como ele deve ser usado requer muito cuidado. Em geral, o código não gerenciado nunca deve ser diretamente exposto a chamadores parcialmente confiáveis. Há duas considerações principais ao avaliar a segurança do uso de código não gerenciado em bibliotecas que podem ser chamadas por código parcialmente confiável:  
  
-   **Funcionalidade**. A API não gerenciada fornece funcionalidade que não permite a chamadores executar operações potencialmente perigosas? A segurança de acesso ao código usa as permissões para impor o acesso aos recursos, portanto, considere se a API usa uma interface do usuário, arquivos ou threading ou se ela expõe informações protegidas. Em caso afirmativo, o código gerenciado que a encapsula deve exigir as permissões necessárias antes de permitir que ela seja inserida. Além disso, embora não protegido por uma permissão, o acesso à memória deve ser restrito à segurança de tipo estrito.  
  
-   **Verificação de parâmetros**. Um ataque comum passa parâmetros inesperados para métodos da API de código não gerenciado expostos em uma tentativa de fazer com que eles operem fora das especificações. Estouros de buffer usando um índice fora do intervalo ou valores de deslocamento são um exemplo comum desse tipo de ataque, assim como o são todos os parâmetros que podem explorar um bug no código subjacente. Portanto, mesmo que a API de código não gerenciado seja funcionalmente segura (após as demandas necessárias) para chamadores parcialmente confiáveis, o código gerenciado também deverá verificar a validade de parâmetros exaustivamente para garantir que nenhuma chamada indesejada seja possível por meio de um código mal-intencionado usando a camada de wrapper de código gerenciado.  
  
## <a name="using-suppressunmanagedcodesecurityattribute"></a>Usando SuppressUnmanagedCodeSecurityAttribute  
 Há um aspecto do desempenho para declarar e, em seguida, chamar código não gerenciado. Para cada uma dessas chamadas, o sistema de segurança automaticamente exige permissão de código não gerenciado, resultando em uma movimentação da pilha a cada vez. Se você declara e imediatamente chama código não gerenciado, a movimentação da pilha pode ser insignificante: ele consiste em sua declaração e chamada de código não gerenciado.  
  
 Um atributo personalizado chamado <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> pode ser aplicado a pontos de entrada de código não gerenciado para desabilitar a verificação de segurança normal, que demanda <xref:System.Security.Permissions.SecurityPermission> com a permissão <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> especificada. É preciso tomar sempre muito cuidado ao fazer isso, porque essa ação cria uma porta aberta em código não gerenciado sem verificações de segurança de tempo de execução. Observe que mesmo com **SuppressUnmanagedCodeSecurityAttribute** aplicado, há uma verificação de segurança única que ocorre durante a compilação JIT (Just-In-Time) para garantir que o chamador imediato tenha permissão para chamar código não gerenciado.  
  
 Se você usar o **SuppressUnmanagedCodeSecurityAttribute**, verifique os seguintes pontos:  
  
-   Verifique o ponto de entrada de código não gerenciado interno ou inacessível fora de seu código.  
  
-   Qualquer chamada para código não gerenciado é uma potencial falha de segurança. Verifique se seu código não é um portal para que código malicioso chame indiretamente código não gerenciado e evite uma verificação de segurança. Solicitar permissões, se apropriado.  
  
-   Use uma convenção de nomenclatura para identificar explicitamente quando você estiver criando um caminho perigoso em código não gerenciado, conforme descrito na seção abaixo.  
  
## <a name="naming-convention-for-unmanaged-code-methods"></a>Convenção de nomenclatura para métodos de código não gerenciado  
 Foi estabelecida uma convenção útil e altamente recomendada para nomear os métodos de código não gerenciado. Todos os métodos de código não gerenciado são separados em três categorias: **seguro**, **nativo** e **não seguro**. Essas palavras-chave podem ser usadas como nomes de classe dentro dos quais os vários tipos de pontos de entrada de código não gerenciado são definidos. No código-fonte, essas palavras-chave devem ser adicionadas ao nome de classe, como em `Safe.GetTimeOfDay`, `Native.Xyz` ou `Unsafe.DangerousAPI`, por exemplo. Cada uma dessas palavras-chave fornece informações de segurança úteis para desenvolvedores que usam essa classe, conforme descrito na tabela a seguir.  
  
|Palavra-chave|Considerações sobre segurança|  
|-------------|-----------------------------|  
|**seguro**|É totalmente inofensivo que qualquer código, até mesmo mal-intencionado, o chame. Pode ser usado exatamente como outro código gerenciado. Por exemplo, uma função que obtém a hora do dia é normalmente segura.|  
|**nativo**|Neutro em termos de segurança, ou seja, código não gerenciado que requer permissão de código não gerenciado para chamar. A segurança é verificada, o que impede um chamador não autorizado.|  
|**unsafe**|Ponto de entrada de código não gerenciado potencialmente perigoso com segurança suprimida. Os desenvolvedores devem ter o máximo de cuidado ao usar código não gerenciado desse tipo, verificando se outras proteções estão em vigor para evitar uma vulnerabilidade de segurança. Os desenvolvedores devem ser responsáveis, pois essa palavra-chave substitui o sistema de segurança.|  
  
## <a name="see-also"></a>Consulte também
- [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)
