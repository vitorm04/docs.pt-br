---
title: Segurança de acesso do código
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b16f169ca61485cf3031076d32178a9407aa54ff
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66488009"
---
# <a name="code-access-security"></a>Segurança de acesso do código
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Sistemas de computador altamente conectado de hoje são expostos com frequência para codificar provenientes de várias, fontes, possivelmente, desconhecidos. Código pode ser anexado ao email, contido em documentos ou baixado pela Internet. Infelizmente, muitos usuários de computador experimentou em primeira mão os efeitos de código móvel mal-intencionado, incluindo vírus e worms, que podem danificar ou destruir dados e o custo do tempo e dinheiro.  
  
 Mecanismos de segurança mais comuns conceder direitos a usuários com base em suas credenciais de logon (normalmente uma senha) e restringem os recursos (muitas vezes os diretórios e arquivos) que o usuário tem permissão para acessar. No entanto, essa abordagem não consegue resolver vários problemas: os usuários obtêm o código de várias fontes, algumas das quais podem não ser confiáveis; o código pode conter bugs ou vulnerabilidades que habilitá-lo para ser explorado por códigos mal-intencionados. e o código, às vezes, faz as coisas que o usuário não sabe que ele faz. Como resultado, os sistemas de computador podem estar danificados e dados privados podem ser perdidos quando os usuários de cuidado e confiáveis executam softwares mal-intencionados ou preenchido de erro. A maioria dos mecanismos de segurança do sistema operacional exigem que cada parte do código deve ser totalmente confiável para executar, exceto, talvez para scripts em uma página da Web. Portanto, ainda há a necessidade de um mecanismo amplamente aplicável que permite que o código de um sistema de computador para executar com a proteção em outro sistema, mesmo quando não há nenhuma relação de confiança entre os sistemas de origem.  
  
 O .NET Framework fornece um mecanismo de segurança denominado segurança de acesso para ajudar a proteger os sistemas contra código mal-intencionado de móvel, para permitir que o código de origens desconhecidas para ser executado com a proteção e para ajudar a evitar código confiável de intencionalmente ou acidentalmente comprometer a segurança. Segurança de acesso do código permite que o código seja confiável em graus variados, dependendo de onde se origina o código e em outros aspectos da identidade do código. Segurança de acesso do código também impõe os vários níveis de confiança no código, o que minimiza a quantidade de código que deve ser totalmente confiável para executar. Usando a segurança de acesso do código pode reduzir a probabilidade de que seu código será mal interpretada por código mal-intencionado ou preenchido de erro. Ele pode reduzir sua responsabilidade, porque você pode especificar o conjunto de operações que seu código deve ter permissão para executar. Segurança de acesso do código também pode ajudar a minimizar os danos que podem resultar de vulnerabilidades de segurança em seu código.  
  
> [!NOTE]
>  Alterações importantes foram feitas para segurança de acesso do código no .NET Framework 4. A alteração mais notável tiver sido [transparência de segurança](../../../docs/framework/misc/security-transparent-code.md), mas também existem outras alterações significativas que afetam a segurança de acesso do código. Para obter informações sobre essas alterações, consulte [alterações de segurança](../../../docs/framework/security/security-changes.md).  
  
 Segurança de acesso do código afeta principalmente aplicativos parcialmente confiáveis e código da biblioteca. Os desenvolvedores de biblioteca devem proteger seu código contra acesso não autorizado de aplicativos parcialmente confiáveis. Aplicativos parcialmente confiáveis são aplicativos que são carregados de fontes externas, como a Internet. Aplicativos que estão instalados em sua área de trabalho ou da intranet local é executado em confiança total. Aplicativos de confiança total não são afetados pela segurança de acesso do código, a menos que eles são marcados como [transparente de segurança](../../../docs/framework/misc/security-transparent-code.md), porque eles são totalmente confiáveis. A única limitação para aplicativos de confiança total é que os aplicativos que são marcados com o <xref:System.Security.SecurityTransparentAttribute> atributo não é possível chamar o código que é marcado com o <xref:System.Security.SecurityCriticalAttribute> atributo. Aplicativos parcialmente confiáveis devem ser executados em uma área restrita (por exemplo, no Internet Explorer) para que possa ser aplicada a segurança de acesso do código. Se você baixa um aplicativo da Internet e tente executá-lo em sua área de trabalho, você obterá um <xref:System.NotSupportedException> com a mensagem: "Foi feita uma tentativa para carregar um assembly de um local de rede que teria causado o assembly a ser área restrita e nas versões anteriores do .NET Framework. Esta versão do .NET Framework não habilitar política de CAS por padrão, portanto, essa carga pode ser perigosa". Se você tiver certeza de que o aplicativo pode ser confiável, você poderá habilitá-lo ser executado em confiança total usando o [ \<loadFromRemoteSources > elemento](../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md). Para obter informações sobre como executar um aplicativo em uma área restrita, consulte [como: Executar o código parcialmente confiável em uma área restrita](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
 Todo o código gerenciado que tem como alvo o common language runtime receba os benefícios de segurança de acesso do código, mesmo que esse código não fazer uma segurança de acesso de código única chamada. Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../../docs/framework/misc/code-access-security-basics.md).  
  
<a name="key_functions"></a>   
## <a name="key-functions-of-code-access-security"></a>Principais funções de segurança de acesso do código  
 Segurança de acesso de código ajuda a limitar o acesso que o código tem a recursos protegidos e operações. No .NET Framework, a segurança de acesso do código realiza as seguintes funções:  
  
- Define as permissões e os conjuntos de permissões que representam o direito de acessar vários recursos do sistema.  
  
- Permite que o código para que os chamadores têm permissões específicas à demanda.  
  
- Permite que o código para que os chamadores possuem uma assinatura digital, permitindo que somente os chamadores de uma organização específica ou um site chamar o código protegido à demanda.  
  
- Impõe restrições em código em tempo de execução, comparando as permissões concedidas de todos os chamadores na pilha de chamadas para as permissões que os chamadores devem ter.  
  
<a name="walking_the_call_stack"></a>   
## <a name="walking-the-call-stack"></a>Movimentar a pilha de chamadas  
 Para determinar se o código está autorizado a acessar um recurso ou executar uma operação, o sistema de segurança do tempo de execução percorre a pilha de chamadas, comparando as permissões concedidas de cada chamador com a permissão está sendo exigida. Se algum chamador na pilha de chamadas não tem a permissão exigida, será gerada uma exceção de segurança e acesso será recusado. A movimentação da pilha é projetada para ajudar a evitar ataques de atração, em que menos confiável código chama código altamente confiável e o utiliza para executar ações não autorizadas. Exigem permissões de todos os chamadores em tempo de execução afeta o desempenho, mas é essencial para ajudar a proteger o código contra ataques de atração pelo código menos confiável. Para otimizar o desempenho, você pode ter seu código executar menos movimentações de pilha; No entanto, você deve ter certeza de não expõem uma vulnerabilidade de segurança, sempre que você fizer isso.  
  
 A ilustração a seguir mostra a movimentação da pilha que resulta quando um método no Assembly A4 exige que os chamadores tenham permissão P.  
  
 ![Segurança de acesso do código](../../../docs/framework/misc/media/slide-10a.gif "slide_10a")  
Movimentação de pilha de segurança  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Noções Básicas da Segurança de Acesso do Código](../../../docs/framework/misc/code-access-security-basics.md)|Descreve a segurança de acesso do código e seus usos mais comuns.|  
|[Código transparente de segurança, nível 2](../../../docs/framework/misc/security-transparent-code-level-2.md)|Descreve o modelo de transparência de segurança no .NET Framework 4.|  
|[Usando bibliotecas de código parcialmente confiável](../../../docs/framework/misc/using-libraries-from-partially-trusted-code.md)|Descreve como habilitar bibliotecas para uso com código não gerenciado e como usar bibliotecas de código não gerenciado.|  
|[Principais conceitos de segurança](../../../docs/standard/security/key-security-concepts.md)|Fornece uma visão geral dos muitos dos principais termos e conceitos usados no sistema de segurança do .NET Framework.|  
|[Segurança baseada em Função](../../../docs/standard/security/role-based-security.md)|Descreve como incorporar a segurança baseada em funções.|  
|[Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)|Descreve como incorporar a criptografia em seus aplicativos.|
