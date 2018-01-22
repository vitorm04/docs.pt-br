---
title: Como localizar assemblies usando DEVPATH
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 0944f2798c45a039149baaa6e46ce2b56eb5c5df
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>Como localizar assemblies usando DEVPATH
Os desenvolvedores talvez queira certificar-se de que um assembly compartilhado que estão criando funciona corretamente com vários aplicativos. Em vez de continuamente colocar o assembly no cache de assembly global durante o ciclo de desenvolvimento, o desenvolvedor pode criar uma variável de ambiente DEVPATH que aponta para o diretório de saída de compilação para o assembly.  
  
 Por exemplo, suponha que você esteja criando um assembly compartilhado chamado MySharedAssembly e o diretório de saída é C:\MySharedAssembly\Debug. Você pode colocar C:\MySharedAssembly\Debug na variável DEVPATH. Você deve especificar o [ \<developmentMode >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) elemento no arquivo de configuração da máquina. Esse elemento indica o common language runtime para usar DEVPATH para localizar assemblies.  
  
 O assembly compartilhado deve ser detectável pelo tempo de execução.  Para especificar uma pasta particular para resolver o uso de referências de assembly a [ \<codeBase > elemento](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) ou [ \<probing > elemento](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) em um arquivo de configuração, conforme descrito em [Especificando o local de um Assembly](../../../docs/framework/configure-apps/specify-assembly-location.md).  Você também pode colocar o assembly em um subdiretório do diretório do aplicativo. Para saber mais, confira [Como o tempo de execução localiza os assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
> [!NOTE]
>  Este é um recurso avançado, destinado apenas para desenvolvimento.  
  
 O exemplo a seguir mostra como fazer com que o tempo de execução procurar por assemblies nos diretórios especificados pela variável de ambiente DEVPATH.  
  
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
>  Use essa configuração somente em tempo de desenvolvimento. O tempo de execução não verifica as versões em assemblies de nomes fortes encontrados no DEVPATH. Ele simplesmente usa o primeiro conjunto que encontrar.  
  
## <a name="see-also"></a>Consulte também  
 [Configuração de aplicativos .NET Framework](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
