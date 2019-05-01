---
title: Utilizando Personificação com segurança de transporte
ms.date: 03/30/2017
ms.assetid: 426df8cb-6337-4262-b2c0-b96c2edf21a9
ms.openlocfilehash: 6209007b60effe5403caf3db8855f029d0c47a0e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050669"
---
# <a name="using-impersonation-with-transport-security"></a>Utilizando Personificação com segurança de transporte
*Representação* é a capacidade de um aplicativo de servidor para assumir a identidade do cliente. É comum para os serviços usam a representação ao validar o acesso aos recursos. O aplicativo de servidor é executado usando uma conta de serviço, mas quando o servidor aceita uma conexão de cliente, ele representa o cliente para que as verificações de acesso são executadas usando as credenciais do cliente. Segurança de transporte é um mecanismo para passar as credenciais e proteger a comunicação usando essas credenciais. Este tópico descreve como usar a segurança de transporte no Windows Communication Foundation (WCF) com o recurso de representação. Para obter mais informações sobre representação usando a segurança de mensagem, consulte [delegação e representação](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="five-impersonation-levels"></a>Cinco níveis de representação  
 Segurança de transporte faz uso de cinco níveis de representação, conforme descrito na tabela a seguir.  
  
|Nível de representação|Descrição|  
|-------------------------|-----------------|  
|Nenhum|O aplicativo de servidor não tenta representar o cliente.|  
|Anônimo|O aplicativo de servidor pode executar verificações de acesso em relação às credenciais do cliente, mas não recebeu nenhuma informação sobre a identidade do cliente. Esse nível de representação é significativo apenas para comunicação na máquina, como pipes nomeados. Usando `Anonymous` com uma conexão remota promove o nível de representação como identificar.|  
|Identificar|O aplicativo de servidor sabe a identidade do cliente e pode executar a validação de acesso em relação às credenciais do cliente, mas não pode representar o cliente. Identificar é o nível de representação padrão usado com as credenciais SSPI no WCF, a menos que o provedor de token fornece um nível de representação diferente.|  
|Impersonate|O aplicativo de servidor pode acessar recursos na máquina do servidor como o cliente, além de realizar verificações de acesso. O aplicativo de servidor não pode acessar recursos em computadores remotos usando a identidade do cliente porque o token de representação não tem credenciais de rede|  
|delegado|Além de ter os mesmos recursos que `Impersonate`, o nível de representação de delegado também permite que o aplicativo de servidor para acessar os recursos em computadores remotos usando a identidade do cliente e para passar a identidade para outros aplicativos.<br /><br /> **Importante** a conta de domínio do servidor deve ser marcada como confiáveis para delegação no controlador de domínio para usar esses recursos adicionais. Esse nível de representação não pode ser usado com contas de domínio do cliente marcadas como confidenciais.|  
  
 Os níveis mais comumente usados com segurança de transporte estão `Identify` e `Impersonate`. Os níveis `None` e `Anonymous` não são recomendados para uso normal, e vários transportes não permitem o uso desses níveis com a autenticação. O `Delegate` nível é um recurso avançado que deve ser usado com cuidado. Somente aplicativos de servidores confiáveis deverá receber a permissão para delegar credenciais.  
  
 Usando a representação na `Impersonate` ou `Delegate` níveis requer que o aplicativo de servidor ter o `SeImpersonatePrivilege` privilégio. Um aplicativo tem esse privilégio por padrão, se ele estiver em execução em uma conta no grupo de administradores ou em uma conta com um SID de serviço (serviço de rede, serviço Local ou sistema Local). Representação não exige a autenticação mútua do cliente e servidor. Alguns esquemas de autenticação que dão suporte a representação, como o NTLM, não podem ser usadas com a autenticação mútua.  
  
## <a name="transport-specific-issues-with-impersonation"></a>Problemas de transporte específicos com a representação  
 A escolha de um transporte no WCF afeta as opções possíveis para a representação. Esta seção descreve problemas que afetam o HTTP padrão e nomeado transportes de pipe no WCF. Transportes personalizados têm suas próprias restrições sobre o suporte para a representação.  
  
### <a name="named-pipe-transport"></a>Chamada de transporte de Pipe  
 Os itens a seguir são usados com o transporte de pipe nomeado:  
  
- O transporte de pipe nomeado é destinado a uso somente no computador local. O transporte de pipe nomeado no WCF explicitamente não permite conexões entre computadores.  
  
- Pipes nomeados não podem ser usados com o `Impersonate` ou `Delegate` nível de representação. O pipe nomeado não pode impor a garantia na máquina nesses níveis de representação.  
  
 Para obter mais informações sobre pipes nomeados, consulte [escolhendo um transporte](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
### <a name="http-transport"></a>Transporte de HTTP  
 As associações que usam o transporte HTTP (<xref:System.ServiceModel.WSHttpBinding> e <xref:System.ServiceModel.BasicHttpBinding>) dão suporte a vários esquemas de autenticação, conforme explicado nas [Noções básicas sobre a autenticação HTTP](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md). A suporte de nível de representação depende do esquema de autenticação. Os itens a seguir são usados com o transporte HTTP:  
  
- O `Anonymous` ignora de esquema de autenticação de representação.  
  
- O `Basic` esquema de autenticação dá suporte apenas a `Delegate` nível. Todos os níveis inferiores de representação são atualizados.  
  
- O `Digest` esquema de autenticação dá suporte apenas a `Impersonate` e `Delegate` níveis.  
  
- O `NTLM` esquema de autenticação, selecionável diretamente ou através de negociação, dá suporte apenas a `Delegate` nível no computador local.  
  
- O esquema de autenticação Kerberos, que só pode ser selecionado por meio de negociação, pode ser usado com qualquer nível de representação com suporte.  
  
 Para obter mais informações sobre o transporte HTTP, consulte [escolhendo um transporte](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
## <a name="see-also"></a>Consulte também

- [Delegação e representação](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
- [Autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
- [Como: Representar um cliente em um serviço](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)
- [Entendendo a autenticação HTTP](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md)
