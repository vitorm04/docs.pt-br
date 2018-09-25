---
title: Como localizar assemblies usando DEVPATH
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 3a9ae9c60ad7de80d04f16984b3b2fb048421cc2
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47080280"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>Como localizar assemblies usando DEVPATH
Talvez os desenvolvedores queiram certificar-se de que um assembly compartilhado que elas estão criando funciona corretamente com vários aplicativos. Em vez de continuamente colocar o assembly no cache de assembly global durante o ciclo de desenvolvimento, o desenvolvedor pode criar uma variável de ambiente DEVPATH que aponta para o diretório de saída de compilação para o assembly.  
  
 Por exemplo, suponha que você esteja criando um assembly compartilhado chamado MySharedAssembly e o diretório de saída é C:\MySharedAssembly\Debug. Você pode colocar C:\MySharedAssembly\Debug na variável DEVPATH. Em seguida, você deve especificar o [ \<developmentMode >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) elemento no arquivo de configuração do computador. Esse elemento informa o common language runtime usar DEVPATH para localizar assemblies.  
  
 O assembly compartilhado deve ser detectável pelo tempo de execução.  Para especificar um diretório particular para resolver referências de assembly usam o [ \<codeBase > elemento](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) ou [ \<probing > elemento](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) em um arquivo de configuração, conforme descrito em [Especificando o local do Assembly](../../../docs/framework/configure-apps/specify-assembly-location.md).  Você também pode colocar o assembly em um subdiretório do diretório do aplicativo. Para saber mais, confira [Como o tempo de execução localiza os assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
> [!NOTE]
>  Isso é um recurso avançado, destinado apenas para desenvolvimento.  
  
 O exemplo a seguir mostra como fazer com que o tempo de execução pesquisa dos assemblies em diretórios especificados pela variável de ambiente DEVPATH.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 Essa configuração padrão é false.  
  
> [!NOTE]
>  Use essa configuração somente em tempo de desenvolvimento. O tempo de execução não verifica as versões de assemblies de nome forte encontrados no DEVPATH. Ela simplesmente usa o assembly primeiro que ele localiza.  
  
## <a name="see-also"></a>Consulte também  
 [Configuração de aplicativos .NET Framework](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
