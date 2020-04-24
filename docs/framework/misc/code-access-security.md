---
title: Segurança de Acesso do Código
ms.date: 03/30/2017
helpviewer_keywords:
- named permission sets, code access security
- call stacks
- malicious code
- stack walk
- security [.NET Framework], code access security
- permissions [.NET Framework], code access security
- trusted code
- mobile code security
- unmanaged code, code access security
- granting permissions, code access security
- user authentication, code access security
- code access security
ms.assetid: 859af632-c80d-4736-8d6f-1e01b09ce127
ms.openlocfilehash: a7dce1efedfb652096e6b583eca08e5b80d282a5
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645787"
---
# <a name="code-access-security"></a>Segurança de Acesso do Código
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Os sistemas de computador altamente conectados de hoje são frequentemente expostos a códigos originários de várias fontes possivelmente desconhecidas. O código pode ser anexado ao e-mail, contido em documentos ou baixado pela Internet. Infelizmente, muitos usuários de computador experimentaram em primeira mão os efeitos do código móvel malicioso, incluindo vírus e worms, que podem danificar ou destruir dados e custar tempo e dinheiro.  
  
 Os mecanismos de segurança mais comuns dão direitos aos usuários com base em suas credenciais de logon (geralmente uma senha) e restringem recursos (muitas vezes diretórios e arquivos) que o usuário pode acessar. No entanto, essa abordagem não resolve vários problemas: os usuários obtêm códigos de muitas fontes, algumas das quais podem não ser confiáveis; o código pode conter bugs ou vulnerabilidades que permitem que ele seja explorado por código malicioso; e código às vezes faz coisas que o usuário não sabe que vai fazer. Como resultado, os sistemas de computador podem ser danificados e dados privados podem ser vazados quando usuários cautelosos e confiáveis executam softwares maliciosos ou cheios de erros. A maioria dos mecanismos de segurança do sistema operacional exige que cada pedaço de código seja completamente confiável para ser executado, exceto talvez para scripts em uma página da Web. Portanto, ainda há a necessidade de um mecanismo de segurança amplamente aplicável que permita que o código originário de um sistema de computador seja executado com proteção em outro sistema, mesmo quando não há relação de confiança entre os sistemas.  
  
 O .NET Framework fornece um mecanismo de segurança chamado segurança de acesso de código para ajudar a proteger os sistemas de computador contra códigos móveis maliciosos, para permitir que códigos de origens desconhecidas corram com proteção e para ajudar a impedir que códigos confiáveis comprometam intencionalmente ou acidentalmente a segurança. A segurança de acesso ao código permite que o código seja confiável em diferentes graus, dependendo da origem do código e de outros aspectos da identidade do código. A segurança de acesso ao código também impõe os diferentes níveis de confiança no código, o que minimiza a quantidade de código que deve ser totalmente confiável para ser executado. O uso da segurança de acesso a código pode reduzir a probabilidade de que seu código seja usado indevidamente por código malicioso ou preenchido por erro. Ele pode reduzir sua responsabilidade, porque você pode especificar o conjunto de operações que seu código deve ser autorizado a realizar. A segurança de acesso ao código também pode ajudar a minimizar os danos que podem resultar de vulnerabilidades de segurança em seu código.  
  
> [!NOTE]
> Foram feitas grandes alterações na segurança de acesso ao código no .NET Framework 4. A mudança mais notável foi [a transparência de segurança,](security-transparent-code.md)mas também há outras mudanças significativas que afetam o segurança de acesso ao código. Para obter informações sobre essas alterações, consulte [Alterações de segurança](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).  
  
 A segurança de acesso ao código afeta principalmente o código da biblioteca e aplicativos parcialmente confiáveis. Os desenvolvedores de bibliotecas devem proteger seu código contra acesso não autorizado contra aplicativos parcialmente confiáveis. Aplicativos parcialmente confiáveis são aplicativos carregados de fontes externas, como a Internet. Os aplicativos instalados na sua área de trabalho ou na intranet local são executados em total confiança. Os aplicativos de confiança total não são afetados pela segurança de acesso ao código, a menos que sejam marcados como [transparentes à segurança,](security-transparent-code.md)porque são totalmente confiáveis. A única limitação para aplicativos de confiança total é <xref:System.Security.SecurityTransparentAttribute> que os aplicativos marcados <xref:System.Security.SecurityCriticalAttribute> com o atributo não podem chamar o código marcado com o atributo. Aplicativos parcialmente confiáveis devem ser executados em uma caixa de areia (por exemplo, no Internet Explorer) para que a segurança de acesso ao código possa ser aplicada. Se você baixar um aplicativo da Internet e tentar executá-lo a partir de sua área de trabalho, você receberá uma <xref:System.NotSupportedException> mensagem com a mensagem: "Uma tentativa foi feita para carregar um conjunto a partir de um local de rede, o que teria feito com que o conjunto fosse sandboxem em versões anteriores do .NET Framework. Esta versão do Quadro .NET não habilita a diretiva CAS por padrão, portanto, essa carga pode ser perigosa." Se você tiver certeza de que o aplicativo pode ser confiável, você pode habilitá-lo a ser executado como confiança total usando o [ \<elemento loadFromRemoteSources>](../configure-apps/file-schema/runtime/loadfromremotesources-element.md). Para obter informações sobre como executar um aplicativo em uma caixa de areia, consulte [Como: Executar código parcialmente confiável em uma caixa de areia](how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
 Todo o código gerenciado que tem como alvo o tempo de execução do idioma comum recebe os benefícios da segurança de acesso ao código, mesmo que esse código não faça uma única chamada de segurança de acesso a código. Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](code-access-security-basics.md).  
  
<a name="key_functions"></a>
## <a name="key-functions-of-code-access-security"></a>Funções-chave do uso de código de acesso  
 A segurança de acesso ao código ajuda a limitar o acesso que o código tem aos recursos e operações protegidas. No .NET Framework, o security de acesso a código executa as seguintes funções:  
  
- Define permissões e conjuntos de permissões que representam o direito de acessar vários recursos do sistema.  
  
- Permite que o código exija que seus chamadores tenham permissões específicas.  
  
- Permite que o código exija que seus chamadores possuam uma assinatura digital, permitindo assim que apenas os chamadores de uma determinada organização ou site chamem o código protegido.  
  
- Impõe restrições ao código no tempo de execução, comparando as permissões concedidas de cada chamador na pilha de chamadas com as permissões que os chamadores devem ter.  
  
<a name="walking_the_call_stack"></a>
## <a name="walking-the-call-stack"></a>Caminhando pela Pilha de Chamadas  
 Para determinar se o código está autorizado a acessar um recurso ou executar uma operação, o sistema de segurança do runtime anda pela pilha de chamadas, comparando as permissões concedidas de cada chamador com a permissão que está sendo exigida. Se qualquer chamador na pilha de chamadas não tiver a permissão exigida, uma exceção de segurança será lançada e o acesso será recusado. A caminhada de pilha foi projetada para ajudar a evitar ataques de atração, nos quais o código menos confiável chama código altamente confiável e o usa para executar ações não autorizadas. Exigir permissões de todos os chamadores em tempo de execução afeta o desempenho, mas é essencial ajudar a proteger o código de atrair ataques por código menos confiável. Para otimizar o desempenho, você pode fazer com que seu código realize menos caminhadas de pilha; no entanto, você deve ter certeza de que você não expõe uma fraqueza de segurança sempre que você faz isso.  
  
 A ilustração a seguir mostra a caminhada de pilha que resulta quando um método na Assembléia A4 exige que seus chamadores tenham permissão P.  
  
 ![Segurança de acesso a código](media/slide-10a.gif "slide_10a")  
Caminhada de pilha de segurança  
  
<a name="related_topics"></a>
## <a name="related-topics"></a>Tópicos Relacionados  
  
|Title|Descrição|  
|-----------|-----------------|  
|[Noções básicas da segurança de acesso do código](code-access-security-basics.md)|Descreve a segurança de acesso ao código e seus usos mais comuns.|  
|[Código transparente de segurança, nível 2](security-transparent-code-level-2.md)|Descreve o modelo de transparência de segurança no Quadro .NET 4.|  
|[Usando bibliotecas de código parcialmente confiável](using-libraries-from-partially-trusted-code.md)|Descreve como habilitar bibliotecas para uso com código não gerenciado e como usar bibliotecas a partir de código não gerenciado.|  
|[Conceitos principais de segurança](../../standard/security/key-security-concepts.md)|Fornece uma visão geral de muitos dos termos e conceitos-chave usados no sistema de segurança .NET Framework.|  
|[Segurança baseada em papéis](../../standard/security/role-based-security.md)|Descreve como incorporar segurança com base em funções.|  
|[Serviços criptográficos](../../standard/security/cryptographic-services.md)|Descreve como incorporar criptografia em seus aplicativos.|
