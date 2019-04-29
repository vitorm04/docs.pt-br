---
title: Funções estáticas globais de fusão
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86cb59c0935c193a9865d5ace5fe11c96226d9e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697713"
---
# <a name="fusion-global-static-functions"></a>Funções estáticas globais de fusão
Esta seção descreve as funções estáticas globais não gerenciadas que usa a API de fusão.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Função ClearDownloadCache](../../../../docs/framework/unmanaged-api/fusion/cleardownloadcache-function.md)  
 Limpa o cache de assembly global de assemblies baixados.  
  
 [Função CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 Compara duas identidades de assembly para determinar se eles são equivalentes.  
  
 [Função CreateApplicationContext](../../../../docs/framework/unmanaged-api/fusion/createapplicationcontext-function.md)  
 Somente interno. (Essa função dá suporte à infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.)  
  
 [Função CreateAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/createassemblycache-function.md)  
 Obtém um ponteiro para um novo [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instância que representa o cache de assembly global.  
  
 [Função CreateAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/createassemblyenum-function.md)  
 Obtém um ponteiro para um [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instância que representa uma lista de objetos que existem no assembly especificado.  
  
 [Função CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 Obtém um ponteiro para um [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instância que representa a identidade exclusiva do assembly com o nome especificado.  
  
 [Função CreateHistoryReader](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 Cria um leitor de histórico para o arquivo especificado.  
  
 [Função CreateInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/createinstallreferenceenum-function.md)  
 Obtém um ponteiro para um [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instância que representa uma lista de referências de um aplicativo para o assembly especificado.  
  
 [Função GetAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/getappidauthority-function.md)  
 Obtém um ponteiro para um [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instância que gerencia as chaves para as identidades de aplicativo e referências.  
  
 [Função GetAssemblyIdentityFromFile](../../../../docs/framework/unmanaged-api/fusion/getassemblyidentityfromfile-function.md)  
 Obtém um ponteiro para um `IUnknown` objeto com especificado `IID` no assembly no caminho de arquivo especificado.  
  
 [Função GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 Obtém o caminho para o assembly em cache, usando os sinalizadores especificados.  
  
 [Função GetHistoryFileDirectory](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 Recupera o caminho do diretório de histórico do aplicativo.  
  
 [Função GetIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/getidentityauthority-function.md)  
 Obtém um ponteiro para um [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instância que gerencia as chaves para objetos de código.  
  
 [Função IsFrameworkAssembly](../../../../docs/framework/unmanaged-api/fusion/isframeworkassembly-function.md)  
 Obtém um valor que indica se o assembly especificado é gerenciado.  
  
 [Função NukeDownloadedCache](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 Exclui o cache de download de tempo de execução de linguagem comum.  
  
 [Função PreBindAssemblyEx](../../../../docs/framework/unmanaged-api/fusion/prebindassemblyex-function.md)  
 Obtém o nome de exibição de pós-política para um assembly.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Interfaces de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
  
 [Enumerações de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [Estruturas de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
  
 [Cache de assembly global](../../../../docs/framework/app-domains/gac.md)
