---
title: "Utilizando Personificação com segurança de transporte"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 426df8cb-6337-4262-b2c0-b96c2edf21a9
caps.latest.revision: "12"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 57b40493d0e9bcbbaaf1366c74ff116343f6ee96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-impersonation-with-transport-security"></a>Utilizando Personificação com segurança de transporte
*Representação* é a capacidade de um aplicativo de servidor para assumir a identidade do cliente. É comum para serviços usar representação ao validar acesso aos recursos. O aplicativo de servidor é executado usando uma conta de serviço, mas quando o servidor aceita uma conexão de cliente, ele representa o cliente para que as verificações de acesso são executadas usando as credenciais do cliente. Segurança de transporte é um mecanismo para passar as credenciais e proteger a comunicação usando essas credenciais. Este tópico descreve como usar a segurança de transporte em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] com o recurso de representação. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]representação usando a segurança de mensagem, consulte [delegação e representação](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="five-impersonation-levels"></a>Cinco níveis de representação  
 Segurança de transporte utiliza cinco níveis de representação, conforme descrito na tabela a seguir.  
  
|Nível de representação|Descrição|  
|-------------------------|-----------------|  
|Nenhum|O aplicativo de servidor não tenta representar o cliente.|  
|Anônimo|O aplicativo de servidor pode executar verificações de acesso em relação às credenciais do cliente, mas não recebeu nenhuma informação sobre a identidade do cliente. Esse nível de representação é significativa apenas para comunicação na máquina, como pipes nomeados. Usando `Anonymous` com uma conexão remota promove o nível de representação para identificar.|  
|Identificar|O aplicativo de servidor sabe a identidade do cliente e pode executar a validação de acesso em relação às credenciais do cliente, mas não é possível representar o cliente. Identificar é o nível de representação padrão usado com as credenciais SSPI em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] , a menos que o provedor de token fornece um nível de representação diferentes.|  
|Impersonate|O aplicativo do servidor pode acessar recursos no computador servidor como o cliente, além de realizar verificações de acesso. O aplicativo de servidor não pode acessar recursos em máquinas remotas usando a identidade do cliente porque o token de representação não tem credenciais de rede|  
|delegado|Além de ter os mesmos recursos `Impersonate`, o nível de representação de representante também permite que o aplicativo do servidor para acessar os recursos em máquinas remotas usando a identidade do cliente e para passar a identidade para outros aplicativos.<br /><br /> **Importante** a conta de domínio do servidor deve ser marcada como confiáveis para delegação no controlador de domínio para usar esses recursos adicionais. Esse nível de representação não pode ser usado com contas de domínio do cliente marcadas como confidenciais.|  
  
 Os níveis mais comumente usados com segurança de transporte são `Identify` e `Impersonate`. Os níveis de `None` e `Anonymous` não são recomendadas para uso normal, e muitas transportes não dão suporte com os níveis de autenticação. O `Delegate` nível é um recurso avançado que deve ser usado com cuidado. Somente os aplicativos de servidor confiável devem receber a permissão para delegar credenciais.  
  
 Usando a representação no `Impersonate` ou `Delegate` níveis requer que o aplicativo de servidor para que o `SeImpersonatePrivilege` privilégio. Um aplicativo tem esse privilégio por padrão, se ele estiver em execução em uma conta no grupo Administradores ou em uma conta com um SID de serviço (serviço de rede, serviço Local ou sistema Local). Representação não exige autenticação mútua do cliente e servidor. Alguns esquemas de autenticação que oferecem suporte a representação, como NTLM, não podem ser usadas com a autenticação mútua.  
  
## <a name="transport-specific-issues-with-impersonation"></a>Problemas de transporte específicos com a representação  
 A escolha de um transporte em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] afeta as opções possíveis para a representação. Esta seção descreve problemas que afetam o HTTP padrão e nomeadas transportes de pipe no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Transportes personalizados têm seus próprios restrições sobre o suporte para representação.  
  
### <a name="named-pipe-transport"></a>Transporte de Pipe de chamada  
 Os itens a seguir são usados com o transporte de pipe nomeado:  
  
-   O transporte de pipe nomeado é destinado ao uso somente no computador local. O transporte de pipe nomeado no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] proíba explicitamente conexões entre computadores.  
  
-   Pipes nomeados não podem ser usados com o `Impersonate` ou `Delegate` nível de representação. O pipe nomeado não é possível impor a garantia na máquina nestes níveis de representação.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]pipes nomeados, consulte [selecionando um transporte](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
### <a name="http-transport"></a>Transporte de HTTP  
 As associações que usam o transporte HTTP (<xref:System.ServiceModel.WSHttpBinding> e <xref:System.ServiceModel.BasicHttpBinding>) dão suporte a vários esquemas de autenticação, conforme explicado em [Noções básicas sobre a autenticação HTTP](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md). A representação de nível de suporte depende do esquema de autenticação. Os itens a seguir são usados com o transporte HTTP:  
  
-   O `Anonymous` ignora de esquema de autenticação de representação.  
  
-   O `Basic` esquema de autenticação oferece suporte apenas a `Delegate` nível. Todos os níveis inferiores de representação são atualizados.  
  
-   O `Digest` esquema de autenticação oferece suporte apenas a `Impersonate` e `Delegate` níveis.  
  
-   O `NTLM` esquema de autenticação, selecionável diretamente ou através de negociação, oferece suporte somente a `Delegate` nível no computador local.  
  
-   O esquema de autenticação Kerberos, que só pode ser selecionado por meio de negociação, pode ser usado com qualquer nível de representação com suporte.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]o transporte HTTP, consulte [selecionando um transporte](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
## <a name="see-also"></a>Consulte também  
 [Delegação e representação](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 [Autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [Como representar um cliente em um serviço](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)  
 [Entendendo a autenticação HTTP](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md)
