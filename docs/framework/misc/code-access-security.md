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
ms.openlocfilehash: e01d3ecf3367baed6673a66015918337105eecb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="code-access-security"></a>Segurança de acesso do código
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Sistemas de computador altamente conectado de hoje com frequência são expostos para codificar provenientes de várias, fontes desconhecidas possivelmente. Código pode ser anexado ao email, contido em documentos ou baixado pela Internet. Infelizmente, muitos usuários de computador tem ficado em primeira mão os efeitos de código móvel mal-intencionado, incluindo vírus e worms, que podem danificar ou destruir dados e tempo e dinheiro.  
  
 Mecanismos de segurança mais comuns conceder direitos a usuários com base em suas credenciais de logon (geralmente uma senha) e restringem os recursos (geralmente diretórios e arquivos) que o usuário tem permissão para acessar. No entanto, essa abordagem não consegue resolver vários problemas: os usuários a obter código de várias fontes, alguns dos quais podem não ser confiáveis; código pode conter bugs ou vulnerabilidades que habilitá-lo para ser explorado por códigos mal-intencionados. e o código faz, às vezes, coisas que o usuário não sabe que isso será feito. Como resultado, os sistemas de computador podem estar danificados e dados privados podem vazar quando usuários cuidados e confiáveis executam software mal-intencionado ou preenchidas com erro. A maioria dos mecanismos de segurança do sistema operacional requerem que cada pedaço de código deve ser totalmente confiável para executar, exceto talvez para scripts em uma página da Web. Portanto, ainda há a necessidade de um mecanismo de segurança amplamente aplicável que permite que o código do sistema de um computador para executar com proteção em outro sistema, mesmo quando não há nenhuma relação de confiança entre os sistemas de origem.  
  
 O .NET Framework fornece um mecanismo de segurança chamado segurança de acesso do código para ajudar a proteger os sistemas de computador de código móvel mal-intencionado, para permitir que o código de origens desconhecidas seja executado com a proteção e para ajudar a evitar código confiável de intencionalmente ou não comprometer a segurança. Segurança de acesso ao código permite que o código se torne confiável em vários graus, dependendo de onde se origina o código e outros aspectos da identidade do código. Segurança de acesso do código também impõe os vários níveis de confiança no código, o que minimiza a quantidade de código que deve ser totalmente confiável para executar. Usando a segurança de acesso de código pode reduzir a probabilidade de que seu código será mal utilizadas por código mal-intencionado ou preenchidas com erro. Isso pode reduzir sua responsabilidade, porque você pode especificar o conjunto de operações que seu código deve ter permissão para executar. Segurança de acesso do código também pode ajudar a minimizar os danos que podem resultar de vulnerabilidades de segurança em seu código.  
  
> [!NOTE]
>  Foram feitas alterações importantes à segurança de acesso do código no [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. A alteração mais notável foi [transparência de segurança](../../../docs/framework/misc/security-transparent-code.md), mas também há outras alterações significativas que afetam a segurança de acesso do código. Para obter informações sobre essas alterações, consulte [alterações de segurança](../../../docs/framework/security/security-changes.md).  
  
 Segurança de acesso do código afeta principalmente aplicativos parcialmente confiáveis e código da biblioteca. Os desenvolvedores de biblioteca devem proteger seu código de acesso não autorizado de aplicativos parcialmente confiáveis. Aplicativos parcialmente confiáveis são aplicativos que são carregados de origens externas, como a Internet. Aplicativos que estão instalados em sua área de trabalho ou da intranet local é executado em confiança total. Aplicativos de confiança total não são afetados pela segurança de acesso do código, a menos que eles serão marcados como [transparência de segurança](../../../docs/framework/misc/security-transparent-code.md), porque eles são totalmente confiáveis. A única limitação para aplicativos de confiança total é que os aplicativos que são marcados com o <xref:System.Security.SecurityTransparentAttribute> atributo não é possível chamar o código que está marcado com o <xref:System.Security.SecurityCriticalAttribute> atributo. Aplicativos parcialmente confiáveis devem ser executados em uma área restrita (por exemplo, no Internet Explorer) para que a segurança de acesso do código pode ser aplicada. Se você baixa um aplicativo da Internet e tente executá-lo da área de trabalho, você obterá um <xref:System.NotSupportedException> com a mensagem: "foi feita uma tentativa de carregar um assembly de um local de rede que faria com o assembly ficasse em versões anteriores do .NET Framework. Nesta versão do .NET Framework não habilitar a política de CAS por padrão, portanto esse carregamento pode ser perigoso." Se você tiver certeza de que o aplicativo pode ser confiável, você poderá habilitá-lo ser executado em confiança total usando o [ \<loadFromRemoteSources > elemento](../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md). Para obter informações sobre como executar um aplicativo em uma área restrita, consulte [como: executar código parcialmente confiável em uma área restrita](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
 Todos os gerenciados de código que tem como alvo o common language runtime recebe os benefícios de segurança de acesso do código, mesmo se esse código não fazer um segurança de acesso ao código única chamada. Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../../docs/framework/misc/code-access-security-basics.md).  
  
<a name="key_functions"></a>   
## <a name="key-functions-of-code-access-security"></a>Principais funções de segurança de acesso ao código  
 Segurança de acesso ao código ajuda a limitar o acesso ao código tem a recursos protegidos e operações. No .NET Framework, a segurança de acesso ao código executa as seguintes funções:  
  
-   Define as permissões e os conjuntos de permissões que representam o direito de acesso a vários recursos do sistema.  
  
-   Permite que o código que os chamadores têm permissões específicas de demanda.  
  
-   Permite que o código que os chamadores tenha uma assinatura digital, permitindo que somente os chamadores de uma determinada organização ou um site chamar o código protegido de demanda.  
  
-   Impõe restrições no código em tempo de execução, comparando as permissões concedidas de todos os chamadores na pilha de chamadas para as permissões que os chamadores devem ter.  
  
<a name="walking_the_call_stack"></a>   
## <a name="walking-the-call-stack"></a>Percorrer a pilha de chamadas  
 Para determinar se o código está autorizado a acessar um recurso ou executar uma operação, o sistema de segurança do tempo de execução orienta a pilha de chamadas, comparando as permissões concedidas de cada chamador as permissões exigidas. Se qualquer chamador na pilha de chamadas não tem a permissão exigida, será gerada uma exceção de segurança e acesso foi recusado. A movimentação da pilha foi projetada para ajudar a evitar ataques de atração, no qual menos confiável código chama o código altamente confiável e o utiliza para executar ações não autorizadas. Exigem permissões de todos os chamadores em tempo de execução afeta o desempenho, mas é essencial para ajudar a proteger o código de ataques de atração pelo código menos confiável. Para otimizar o desempenho, você pode ter seu código executar menos movimentações de pilha; No entanto, você deve ter certeza de que não expõem uma vulnerabilidade de segurança sempre que você fizer isso.  
  
 A ilustração a seguir mostra a movimentação da pilha que ocorre quando um método no Assembly A4 exige que os chamadores tem permissão P.  
  
 ![Segurança de acesso ao código](../../../docs/framework/misc/media/slide-10a.gif "slide_10a")  
Movimentação de pilha de segurança  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Noções Básicas da Segurança de Acesso do Código](../../../docs/framework/misc/code-access-security-basics.md)|Descreve a segurança de acesso do código e seus usos mais comuns.|  
|[Código transparente de segurança, nível 2](../../../docs/framework/misc/security-transparent-code-level-2.md)|Descreve o modelo de transparência de segurança no [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].|  
|[Usando bibliotecas de código parcialmente confiável](../../../docs/framework/misc/using-libraries-from-partially-trusted-code.md)|Descreve como habilitar bibliotecas para uso com código não gerenciado e como usar bibliotecas de código não gerenciado.|  
|[Principais conceitos de segurança](../../../docs/standard/security/key-security-concepts.md)|Fornece uma visão geral dos muitos dos principais termos e conceitos usados no sistema de segurança do .NET Framework.|  
|[Segurança baseada em Função](../../../docs/standard/security/role-based-security.md)|Descreve como incorporar a segurança baseada em funções.|  
|[Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)|Descreve como incorporar a criptografia em seus aplicativos.|
