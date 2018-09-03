---
title: Migrar do .NET Framework 1.1
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, migrating from 1.1
- .NET Framework 1.1, migrating to .NET Framework 4.5
ms.assetid: 7ead0cb3-3b19-414a-8417-a1c1fa198d9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc3c611cf043538e7f069cc1634bd5be5e70dfab
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43392270"
---
# <a name="migrating-from-the-net-framework-11"></a>Migrar do .NET Framework 1.1
[!INCLUDE[win7](../../../includes/win7-md.md)] e versões posteriores do sistema operacional Windows não oferecem suporte ao [!INCLUDE[net_v11_long](../../../includes/net-v11-long-md.md)]. Assim, os aplicativos destinados ao [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] não serão executados sem modificação no [!INCLUDE[win7](../../../includes/win7-md.md)] ou em versões posteriores do sistema operacional. Este tópico discute as etapas necessárias para executar um aplicativo que se destina ao [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] no [!INCLUDE[win7](../../../includes/win7-md.md)] e em versões posteriores do sistema operacional Windows. Para saber mais sobre o [!INCLUDE[net_v11_long](../../../includes/net-v11-long-md.md)] e o [!INCLUDE[win8](../../../includes/win8-md.md)], veja [Executar aplicativos .NET Framework 1.1 no Windows 8 e versões posteriores](../../../docs/framework/install/run-net-framework-1-1-apps.md).  
  
## <a name="retargeting-or-recompiling"></a>Redirecionando ou recompilando  
 Existem duas maneiras de fazer um aplicativo compilado usando-se o [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] ser executado no [!INCLUDE[win7](../../../includes/win7-md.md)] ou em versões posteriores do sistema operacional Windows:  
  
-   Você pode redirecionar o aplicativo a ser executado no [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. O redirecionamento exige que você adicione um elemento [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) ao arquivo de configuração do aplicativo que permite que ele seja executado no [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. Esse arquivo de configuração utiliza a seguinte forma:  
  
    ```xml  
    <configuration>   
       <startup>  
          <supportedRuntime version="v4.0"/>  
       </startup>  
    </configuration>  
    ```  
  
-   Você pode recompilar o aplicativo com um compilador que tem como alvo o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. Se tiver usado originalmente o Visual Studio 2003 para desenvolver e compilar sua solução, você poderá abrir a solução no [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] e usar a caixa de diálogo **Compatibilidade do Projeto** para converter a solução e os arquivos do projeto dos formatos usados pelo Visual Studio 2003 para o formato MSBuild (Microsoft Build Engine) usado pelo [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)].  
  
 Independentemente de preferir recompilar ou redirecionar seu aplicativo, você deve determinar se o aplicativo é afetado por alguma alterações introduzida em versões posteriores do .NET Framework. Essas alterações são de dois tipos:  
  
-   Alterações significativas ocorridas entre o [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] e as versões posteriores do .NET Framework.  
  
-   Tipos e membros do tipo que foram marcados como substituídos ou obsoletos entre o [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] e as versões posteriores do .NET Framework.  
  
 Se redirecionar seu aplicativo ou recompilá-lo, você deverá examinar as alterações significativas e os tipos e membros obsoletos de cada versão do .NET Framework liberada após o [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)].  
  
## <a name="breaking-changes"></a>Alterações significativas  
 Quando ocorre uma alteração significativa, dependendo da alteração específica, a solução desse problema pode estar disponível tanto para aplicativos redestinados como para recompilados. Em alguns casos, você pode adicionar um elemento filho para o elemento [\<runtime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) do seu arquivo de configuração do aplicativo para restaurar o comportamento anterior. Por exemplo, o arquivo de configuração restaura a classificação da cadeia de caracteres e o comportamento usado no [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] e podem ser usados com um aplicativo redestinado ou recompilado.  
  
```xml  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
 No entanto, em alguns casos, você talvez tenha que modificar o código-fonte e recompilar seu aplicativo.  
  
 Para avaliar o impacto de alterações significativas possíveis em seu aplicativo, você deve examinar a seguinte lista de alterações:  
  
-   [Alterações significativas no .NET Framework 2.0](https://go.microsoft.com/fwlink/?LinkId=125263) documenta alterações no [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] que podem afetar um aplicativo destinado ao [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)].  
  
-   [Alterações no .NET Framework 3.5 SP1](https://go.microsoft.com/fwlink/?LinkID=186989) documenta alterações entre o[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] e o [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)].  
  
-   [Problemas de migração do .NET Framework 4](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md) documenta alterações entre o [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] e o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
## <a name="obsolete-types-and-members"></a>Tipos e membros obsoletos  
 O impacto de tipos e membros substituídos é um pouco diferente para aplicativos redirecionados e aplicativos recompilados. O uso de tipos e de membros obsoletos não afetará um aplicativo que foi escolhido novamente como destino, a menos que o tipo ou membro obsoleto tenha sido removido fisicamente do assembly. A recompilação de um aplicativo que usa tipos ou associados obsoletos geralmente resulta em um aviso de compilador, em vez de um erro do compilador. No entanto, em alguns casos, ele produz um erro do compilador, e o código que usa o tipo ou membro obsoleto não é compilado com êxito. Neste caso, você deve reescrever o código-fonte que chama o tipo ou membro obsoleto antes de recompilar seu aplicativo. Para saber mais sobre os tipos e membros obsoletos, veja [O que está obsoleto na Biblioteca de Classes](../../../docs/framework/whats-new/whats-obsolete.md).  
  
 Para avaliar o impacto dos tipos e membros que foram substituídos desde o lançamento do [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)], veja [O que está obsoleto na Biblioteca de Classes](../../../docs/framework/whats-new/whats-obsolete.md). Examine as listas de tipos e de membros obsoletos do [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)], do [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] e do [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].
