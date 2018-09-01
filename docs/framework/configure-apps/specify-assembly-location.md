---
title: Especificando um Assembly&#39;s local
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4a83f1e67377a5ce699301770ff0369f8f760884
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43387322"
---
# <a name="specifying-an-assembly39s-location"></a>Especificando um Assembly&#39;s local
Há duas maneiras para especificar o local de um assembly:  
  
-   Usando o [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elemento.  
  
-   Usando o [ \<probing >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elemento.  
  
 Você também pode usar o [.NET Framework Configuration Tool (Mscorcfg. msc)](https://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764) para especificar locais de assembly ou especificar locais para o common language runtime investigar assemblies.  
  
## <a name="using-the-codebase-element"></a>Usando o \<codeBase > elemento  
 Você pode usar o  **\<codeBase >** elemento apenas na máquina configuração ou publicador arquivos de política que também redirecionar a versão do assembly. Quando o tempo de execução determina qual versão de assembly a ser usada, ela se aplica a configuração de base de código do arquivo que determina a versão. Se nenhuma base de código estiver indicado, o tempo de execução investiga o assembly da maneira normal. Para obter detalhes, consulte [como o tempo de execução Localiza Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 O exemplo a seguir mostra como especificar o local de um assembly.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <codeBase version="2.0.0.0"  
                   href="http://www.litwareinc.com/myAssembly.dll"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 O **versão** atributo é necessário para todos os assemblies de nome forte, mas deve ser omitido para assemblies que não são forte. O  **\<codeBase >** elemento requer o **href** atributo. Não é possível especificar intervalos de versão na  **\<codeBase >** elemento.  
  
> [!NOTE]
>  Se você estiver fornecendo uma referência de base de código para um assembly que não é forte, a dica deve apontar para a base do aplicativo ou em um subdiretório do diretório base do aplicativo.  
  
## <a name="using-the-probing-element"></a>Usando o \<probing > elemento  
 O tempo de execução localiza assemblies que não têm uma base de código por sondagem. Para obter mais informações sobre a investigação, consulte [como o tempo de execução Localiza Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Você pode usar o [ \<probing >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elemento no arquivo de configuração de aplicativo para especificar o tempo de execução deve pesquisar para localizar um assembly de subdiretórios. O exemplo a seguir mostra como especificar diretórios de que tempo de execução deve pesquisar.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 O **privatePath** atributo contém os diretórios que o tempo de execução deve procurar assemblies. Se o aplicativo está localizado em C:\Program MyApp, o tempo de execução procura assemblies que não especificam uma base de código em C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin e C:\Program Files\MyApp\Bin3. Diretórios especificados em **privatePath** devem ser subdiretórios do diretório base do aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Assemblies no Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [Programação com assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [Como o tempo de execução localiza assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Configuração de aplicativos .NET Framework](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
