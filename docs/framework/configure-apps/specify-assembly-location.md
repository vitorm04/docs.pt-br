---
title: Especificando o local de um assembly
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: f13b19dcd0aceac969d9639e6230ad33c6cd8d84
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971545"
---
# <a name="specifying-an-assemblys-location"></a>Especificando o local de um assembly
Há duas maneiras de especificar o local de um assembly:  
  
- Usando o [ \<elemento > codebase](./file-schema/runtime/codebase-element.md) .  
  
- Usando o elemento de [ \<> de investigação](./file-schema/runtime/probing-element.md) .  
  
 Você também pode usar a [ferramenta de configuração de .NET Framework (Mscorcfg. msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) para especificar locais de assembly ou especificar locais para o Common Language Runtime investigar para assemblies.  
  
## <a name="using-the-codebase-element"></a>Usando o \<elemento > codebase  
 Você pode usar o  **\<elemento > codebase** somente em configuração do computador ou em arquivos de política do Publicador que também redirecionem a versão do assembly. Quando o tempo de execução determina qual versão de assembly usar, ele aplica a configuração de base do código do arquivo que determina a versão. Se nenhuma base de código for indicada, o tempo de execução investigará o assembly da maneira normal. Para obter detalhes, consulte [como o tempo de execução localiza assemblies](../deployment/how-the-runtime-locates-assemblies.md).  
  
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
  
 O atributo **version** é necessário para todos os assemblies de nome forte, mas deve ser omitido para assemblies que não são de nome forte. **O\<elemento > codebase** requer o atributo **href** . Você não pode especificar intervalos de versão no  **\<elemento > codebase** .  
  
> [!NOTE]
> Se você estiver fornecendo uma dica de base de código para um assembly que não seja de nome forte, a dica deverá apontar para a base do aplicativo ou um subdiretório do diretório base do aplicativo.  
  
## <a name="using-the-probing-element"></a>Usando o \<elemento de > de investigação  
 O tempo de execução localiza assemblies que não têm uma base de código por investigação. Para obter mais informações sobre investigação, consulte [como o tempo de execução localiza assemblies](../deployment/how-the-runtime-locates-assemblies.md).  
  
 Você pode usar o [ \<](./file-schema/runtime/probing-element.md) elemento de > de investigação no arquivo de configuração do aplicativo para especificar subdiretórios que o tempo de execução deve pesquisar ao localizar um assembly. O exemplo a seguir mostra como especificar diretórios que o tempo de execução deve pesquisar.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 O atributo **privatePath** contém os diretórios em que o tempo de execução deve pesquisar assemblies. Se o aplicativo estiver localizado em C:\Program MyApp, o tempo de execução procurará assemblies que não especificam uma base de código em C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin e C:\Program Files\MyApp\Bin3. Os diretórios especificados em **privatePath** devem ser subdiretórios do diretório base do aplicativo.  
  
## <a name="see-also"></a>Consulte também

- [Assemblies no .NET](../../standard/assembly/index.md)
- [Programação com assemblies](../../standard/assembly/program.md)
- [Como o tempo de execução localiza assemblies](../deployment/how-the-runtime-locates-assemblies.md)
- [Configurando aplicativos usando arquivos de configuração](index.md)
