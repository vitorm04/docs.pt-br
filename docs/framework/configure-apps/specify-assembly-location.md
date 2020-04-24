---
title: Especificando o local de um assembly
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: ead69d1e850050214c15295134c06ff6f66e9760
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646026"
---
# <a name="specifying-an-assemblys-location"></a>Especificando o local de um assembly
Existem duas maneiras de especificar a localização de uma montagem:  
  
- Usando [ \<](./file-schema/runtime/codebase-element.md) o elemento codeBase>.  
  
- Usando [ \<](./file-schema/runtime/probing-element.md) o elemento>sondagem.  
  
 Você também pode usar a [Ferramenta de Configuração do Framework .NET (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) para especificar locais de montagem ou especificar locais para o tempo de execução do idioma comum para sondar para conjuntos.  
  
## <a name="using-the-codebase-element"></a>Usando \<o elemento codeBase>  
 Você pode ** \<** usar o elemento codeBase>apenas em arquivos de configuração de máquina ou diretiva de editor que também redirecionam a versão de montagem. Quando o tempo de execução determina qual versão de montagem deve ser usada, ele aplica a configuração base de código do arquivo que determina a versão. Se nenhuma base de código for indicada, os testes de tempo de execução para a montagem da maneira normal. Para obter detalhes, [consulte Como o Runtime localiza montagens](../deployment/how-the-runtime-locates-assemblies.md).  
  
 O exemplo a seguir mostra como especificar a localização de um conjunto.  
  
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
  
 O atributo de **versão** é necessário para todos os conjuntos com nome forte, mas deve ser omitido para conjuntos que não são fortes. O ** \<** elemento codeBase>requer o atributo **href.** Não é possível especificar ** \<** faixas de versão no elemento codeBase>.  
  
> [!NOTE]
> Se você estiver fornecendo uma dica de base de código para um conjunto que não tenha um nome forte, a dica deve apontar para a base de aplicativos ou um subdiretório do diretório base de aplicativos.  
  
## <a name="using-the-probing-element"></a>Usando \<o elemento> sondagem  
 O tempo de execução localiza conjuntos que não possuem uma base de código por sondagem. Para obter mais informações sobre a sondagem, consulte [Como o Runtime Localiza Montagens](../deployment/how-the-runtime-locates-assemblies.md).  
  
 Você pode [ \<](./file-schema/runtime/probing-element.md) usar o elemento de>de sondagem no arquivo de configuração do aplicativo para especificar subdiretórios que o tempo de execução deve pesquisar ao localizar um conjunto. O exemplo a seguir mostra como especificar diretórios que o tempo de execução deve ser pesquisado.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 O atributo **privatePath** contém os diretórios que o tempo de execução deve procurar montagens. Se o aplicativo estiver localizado em C:\Program Files\MyApp, o tempo de execução procurará conjuntos que não especifiquem uma base de código em C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin e C:\Program Files\MyApp\Bin3. Os diretórios especificados no **privatePath** devem ser subdiretórios do diretório base de aplicativos.  
  
## <a name="see-also"></a>Confira também

- [Assemblies no .NET](../../standard/assembly/index.md)
- [Programação com assemblies](../../standard/assembly/index.md)
- [Como o runtime localiza assemblies](../deployment/how-the-runtime-locates-assemblies.md)
- [Configurando aplicativos usando arquivos de configuração ](index.md)
