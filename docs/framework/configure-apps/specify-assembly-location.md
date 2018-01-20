---
title: Especificando um Assembly &#39; s local
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4cfe8752ce3a562e1e4b576c63b56ff56255ff62
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="specifying-an-assembly39s-location"></a>Especificando um Assembly &#39; s local
Há duas maneiras de especificar o local de um assembly:  
  
-   Usando o [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elemento.  
  
-   Usando o [ \<probing >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elemento.  
  
 Você também pode usar o [ferramenta de configuração do .NET Framework (Mscorcfg.msc)](http://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764) para especificar locais de assembly ou especificar locais para o common language runtime para investigação para assemblies.  
  
## <a name="using-the-codebase-element"></a>Usando o \<codeBase > elemento  
 Você pode usar o  **\<codeBase >** elemento apenas na configuração ou publicador política arquivos de máquina que redirecionam também a versão do assembly. Quando o tempo de execução determina qual versão do assembly a ser usado, ele se aplica a configuração de base de código do arquivo que determina a versão. Se nenhuma base de código é indicado, o tempo de execução de testes para o assembly da maneira normal. Para obter detalhes, consulte [como o tempo de execução Localiza Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
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
  
 O **versão** atributo é necessário para todos os assemblies de nomes fortes, mas devem ser omitido para assemblies que não são fortes. O  **\<codeBase >** elemento requer o **href** atributo. Você não pode especificar intervalos de versão no  **\<codeBase >** elemento.  
  
> [!NOTE]
>  Se você está fornecendo uma referência de base de código para um assembly que não está com nome forte, a dica deve apontar para a base de dados de aplicativo ou em um subdiretório do diretório base do aplicativo.  
  
## <a name="using-the-probing-element"></a>Usando o \<probing > elemento  
 O tempo de execução localiza assemblies que não tem uma base de código por sondagem. Para obter mais informações sobre a sondagem, consulte [como o tempo de execução Localiza Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Você pode usar o [ \<probing >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elemento no arquivo de configuração do aplicativo para especificar o tempo de execução deve pesquisar para localizar um assembly de subdiretórios. O exemplo a seguir mostra como especificar diretórios que deve pesquisar o tempo de execução.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 O **privatePath** atributo contém os diretórios que o tempo de execução deve procurar por assemblies. Se o aplicativo está localizado em MyApp C:\Program, o tempo de execução procurará assemblies que não especificam uma base de código em C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin e C:\Program Files\MyApp\Bin3. Diretórios especificados em **privatePath** devem ser subdiretórios do diretório base do aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Assemblies no Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [Programação com assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [Como o tempo de execução localiza assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Configuração de aplicativos .NET Framework](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
