---
title: 'Como: Localizar assemblies usando DEVPATH'
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 6fa864f814d6a9ce04f2bce92c61cd0075ab5145
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912995"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>Como: Localizar assemblies usando DEVPATH
Os desenvolvedores podem querer ter certeza de que um assembly compartilhado que está compilando funciona corretamente com vários aplicativos. Em vez de colocar continuamente o assembly no cache de assembly global durante o ciclo de desenvolvimento, o desenvolvedor pode criar uma variável de ambiente DEVPATH que aponta para o diretório de saída da compilação para o assembly.  
  
 Por exemplo, suponha que você esteja criando um assembly compartilhado chamado MySharedAssembly e o diretório de saída seja C:\MySharedAssembly\Debug. Você pode colocar C:\MySharedAssembly\Debug na variável DEVPATH. Em seguida, você deve especificar o elemento de [ \<> developmentmode](./file-schema/runtime/developmentmode-element.md) no arquivo de configuração do computador. Esse elemento informa ao Common Language Runtime usar DEVPATH para localizar assemblies.  
  
 O assembly compartilhado deve ser detectável pelo tempo de execução.  Para especificar um diretório privado para resolver referências de assembly, use o elemento [ \<> codebase](./file-schema/runtime/codebase-element.md) ou [ \<o elemento > de investigação](./file-schema/runtime/probing-element.md) em um arquivo de configuração, conforme descrito em [especificando o local de um assembly](specify-assembly-location.md).  Você também pode colocar o assembly em um subdiretório do diretório do aplicativo. Para saber mais, confira [Como o tempo de execução localiza os assemblies](../deployment/how-the-runtime-locates-assemblies.md).  
  
> [!NOTE]
> Esse é um recurso avançado, destinado apenas ao desenvolvimento.  
  
 O exemplo a seguir mostra como fazer com que o tempo de execução procure por assemblies em diretórios especificados pela variável de ambiente DEVPATH.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 Essa configuração assume como padrão false.  
  
> [!NOTE]
> Use essa configuração somente no momento do desenvolvimento. O tempo de execução não verifica as versões em assemblies de nome forte encontrados no DEVPATH. Ele simplesmente usa o primeiro assembly que encontra.  
  
## <a name="see-also"></a>Consulte também

- [Configurando aplicativos usando arquivos de configuração](index.md)
