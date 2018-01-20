---
title: "Permissão de segurança para redirecionamento de associações de assemblies"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d2593df04b93db17f9ca61a98b21aaec1d534d46
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="assembly-binding-redirection-security-permission"></a>Permissão de segurança para redirecionamento de associações de assemblies
O redirecionamento de associação de assembly explícito em um arquivo de configuração do aplicativo requer uma permissão de segurança. Isso se aplica ao redirecionamento de assemblies do .NET Framework e assemblies de terceiros. A permissão é concedida, definindo o <xref:System.Security.Permissions.SecurityPermissionFlag> sinalizador no <xref:System.Security.Permissions.SecurityPermission>. Assemblies gerenciados não têm permissões por padrão.  
  
 É concedida a permissão de segurança para aplicativos em execução nas zonas confiáveis (computador local) e zona da Intranet. Aplicativos em execução na zona da Internet são estritamente proibidos de realizar o redirecionamento de associação de assembly.  
  
 A permissão não é necessária se o redirecionamento de assembly é executado em um arquivo de política de editor é controlado pelo editor de componente, ou no arquivo de configuração da máquina é controlado pelo administrador. No entanto, a permissão é necessária para um aplicativo ignorar explicitamente a política de publicador usando o [ \<publisherPolicy aplicar = "no" / >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) elemento no arquivo de configuração do aplicativo.  
  
 A tabela a seguir mostra o padrão de configurações de segurança para o **BindingRedirects** sinalizador.  
  
|Zona|Configuração do sinalizador de BindingRedirects|  
|----------|-----------------------------------|  
|Zona confiável (computador local)|**ON**|  
|Zona de intranet|**ON**|  
|Zona da Internet|**OFF**|  
|Zonas não confiáveis|**OFF**|  
  
 Um administrador pode alterar essas configurações de segurança para oferecer suporte ou restringir cenários específicos em um determinado computador. Não há ferramentas para alterar o **BindingRedirects** sinalizador definindo o padrão; um administrador deve editar manualmente o arquivo Security config no computador do usuário.  
  
## <a name="see-also"></a>Consulte também  
 [Arquivos de política do publicador e execução lado a lado](http://msdn.microsoft.com/library/97a042be-4d72-40c3-91c0-76fd36bdf133)  
 [Como habilitar e desabilitar o redirecionamento automático de associações](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [Execução lado a lado](../../../docs/framework/deployment/side-by-side-execution.md)
