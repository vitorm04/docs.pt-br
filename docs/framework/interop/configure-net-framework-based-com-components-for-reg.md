---
title: Como configurar componentes do COM baseados no .NET Framework para ativação sem registro
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 744ce1f2810eee025f071cafaa71e473b6ed4c50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a>Como configurar componentes do COM baseados no .NET Framework para ativação sem registro
A ativação sem registro de componentes baseados no .NET Framework é apenas um pouco mais complicada do que para componentes COM. A instalação exige dois manifestos:  
  
-   Os aplicativos COM devem ter um manifesto do aplicativo no estilo Win32 para identificar o componente gerenciado.  
  
-   Os componentes baseados no .NET Framework devem ter um manifesto do componente para obter as informações de ativação necessárias em tempo de execução.  
  
 Este tópico descreve como associar um manifesto do aplicativo a um aplicativo, associar um manifesto do componente a um componente e inserir um manifesto do componente em um assembly.  
  
### <a name="to-create-an-application-manifest"></a>Para criar um manifesto do aplicativo  
  
1.  Usando um editor de XML, crie (ou modifique) o manifesto do aplicativo pertencente ao aplicativo COM que interopera com um ou mais componentes gerenciados.  
  
2.  Insira o seguinte cabeçalho padrão no início do arquivo:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     Para obter informações sobre seus atributos e elementos de manifesto, consulte [manifestos de aplicativo](https://msdn.microsoft.com/library/windows/desktop/aa374191.aspx).  
  
3.  Identifique o proprietário do manifesto. No exemplo a seguir, `myComApp` versão 1 possui o arquivo de manifesto.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4.  Identifique os assemblies dependentes. No exemplo a seguir, `myComApp` depende de `myManagedComp`.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="x86"   
                        publicKeyToken="8275b28176rcbbef"  
      />  
      <dependency>  
        <dependentAssembly>  
          <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myManagedComp"   
                        version="6.0.0.0"   
                        processorArchitecture="X86"   
                        publicKeyToken="8275b28176rcbbef"  
          />  
        </dependentAssembly>  
      </dependency>  
    </assembly>  
    ```  
  
5.  Salve e nomeie o arquivo de manifesto. O nome de um manifesto do aplicativo é o nome do executável do assembly seguido pela extensão .manifest. Por exemplo, o nome do arquivo de manifesto do aplicativo para myComApp.exe é myComApp.exe.manifest.  
  
 Você pode instalar um manifesto do aplicativo no mesmo diretório do aplicativo COM. Como alternativa, adicione-o como um recurso ao arquivo .exe do aplicativo. Para obter informações adicionais, para obter mais informações, consulte [sobre Assemblies lado a lado](https://msdn.microsoft.com/library/windows/desktop/ff951640.aspx).  
  
#### <a name="to-create-a-component-manifest"></a>Para criar um manifesto do componente  
  
1.  Usando um editor de XML, crie um manifesto do componente para descrever o assembly gerenciado.  
  
2.  Insira o seguinte cabeçalho padrão no início do arquivo:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3.  Identifique o proprietário do arquivo. O elemento `<assemblyIdentity>` do elemento `<dependentAssembly>` no arquivo de manifesto do aplicativo deve corresponder àquele no manifesto do componente. No exemplo a seguir, `myManagedComp` versão 1.2.3.4 possui o arquivo de manifesto.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />  
    ```  
  
4.  Identifique cada classe no assembly. Use o elemento `<clrClass>` para identificar cada classe exclusivamente no assembly gerenciado. O elemento, que é um subelemento do elemento `<assembly>`, tem os atributos descritos na tabela a seguir.  
  
    |Atributo|Descrição|Necessária|  
    |---------------|-----------------|--------------|  
    |`clsid`|O identificador que especifica a classe a ser ativada.|Sim|  
    |`description`|Uma cadeia de caracteres que informa o usuário sobre o componente. Uma cadeia de caracteres vazia é o padrão.|Não|  
    |`name`|Uma cadeia de caracteres que representa a classe gerenciada.|Sim|  
    |`progid`|O identificador a ser usado para a ativação de associação tardia.|Não|  
    |`threadingModel`|O modelo de threading COM. “Ambos” é o valor padrão.|Não|  
    |`runtimeVersion`|Especifica a versão do CLR (Common Language Runtime) a ser usada. Se você não especificar esse atributo e o CLR ainda não estiver carregado, o componente será carregado com o último CLR instalado anterior ao CLR versão 4. Se você especificar v1.0.3705, v1.1.4322 ou v2.0.50727, a versão efetuará roll forward automaticamente até a última versão instalada do CLR anterior ao CLR versão 4 (geralmente, v2.0.50727). Se outra versão do CLR já estiver carregada e a versão especificada puder ser carregada lado a lado no processo, a versão especificada será carregada; caso contrário, o CLR carregado será usado. Isso poderá causar uma falha de carregamento.|Não|  
    |`tlbid`|O identificador da biblioteca de tipos que contém informações sobre a classe.|Não|  
  
     Todas as marcações de atributo diferenciam maiúsculas de minúsculas. É possível obter CLSIDs, ProgIDs, modelos de threading e a versão de tempo de execução exibindo a biblioteca de tipos exportada para o assembly com o ObjectViewer OLE/COM (Oleview.exe).  
  
     O manifesto do componente a seguir identifica duas classes, `testClass1` e `testClass2`.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"   
                        publicKeyToken="8275b28176rcbbef"  
           />  
           <clrClass  
                        clsid="{65722BE6-3449-4628-ABD3-74B6864F9739}"  
                        progid="myManagedComp.testClass1"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass1"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <clrClass  
                        clsid="{367221D6-3559-3328-ABD3-45B6825F9732}"  
                        progid="myManagedComp.testClass2"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass2"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <file name="MyManagedComp.dll">  
           </file>  
    </assembly>  
    ```  
  
5.  Salve e nomeie o arquivo de manifesto. O nome de um manifesto do componente é o nome da biblioteca de assemblies seguido pela extensão .manifest. Por exemplo, a myManagedComp.dll é myManagedComp.manifest.  
  
 É necessário inserir o manifesto do componente como um recurso no assembly.  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a>Para inserir um manifesto do componente em um assembly gerenciado  
  
1.  Crie um script de recurso que contém a seguinte instrução:  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     Nessa instrução, `myManagedComp.manifest` é o nome do manifesto do componente que está sendo inserido. Neste exemplo, o nome do arquivo de script é `myresource.rc`.  
  
2.  Compile o script usando o Compilador de Recurso do Microsoft Windows (Rc.exe). No prompt de comando, digite o seguinte comando:  
  
     `rc myresource.rc`  
  
     O Rc.exe gera o arquivo de recurso `myresource.res`.  
  
3.  Compile o arquivo de origem do assembly novamente e especifique o arquivo de recurso usando a opção **/win32res**:  
  
    ```  
    /win32res:myresource.res  
    ```  
  
     Novamente, `myresource.res` é o nome do arquivo de recurso que contém o recurso inserido.  
  
## <a name="see-also"></a>Consulte também  
 [Interoperabilidade COM sem registro](registration-free-com-interop.md)  
 [Requisitos para interoperabilidade COM sem registro](https://msdn.microsoft.com/library/0c43bc57-eecf-4e6c-8114-490141cce4da(v=vs.100)))  
 [Configurando componentes COM sem registro de ativação de](https://msdn.microsoft.com/library/bfe9b02f-d964-4784-960e-a1f94692fbfe(v=vs.100)))  
 [Ativação sem registro de componentes baseados no .NET: um passo a passo](https://msdn.microsoft.com/library/ms973915.aspx)
