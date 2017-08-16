---
title: Gacutil.exe (Ferramenta do Cache de Assembly Global) | Microsoft Docs
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- global assembly cache, manipulating contents
- GAC (global assembly cache), Gacutil.exe
- Gacutil.exe
- GAC (global assembly cache), viewing contents
- installing assemblies into global assembly cache
- removing assemblies from global assembly cache
- list of assemblies in global assembly cache
- cache [.NET Framework], global assembly cache
- GAC (global assembly cache), manipulating contents
- global assembly cache, Gacutil.exe
- Global Assembly Cache tool
ms.assetid: 4c7be9c8-72ae-481f-a01c-1a4716806e99
caps.latest.revision: 17
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 006048026503c8a3e9d1f1a62a1ae67ff2c03ae9
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---
# <a name="gacutilexe-global-assembly-cache-tool"></a>Gacutil.exe (Ferramenta do Cache de Assemblies Global)
A ferramenta de Cache de Assembly Global permite exibir e manipular o conteúdo do cache de assembly global e do cache de download.  
  
 Essa ferramenta é instalada automaticamente com o Visual Studio. Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor (ou o Prompt de Comando do Visual Studio no Windows 7). Para obter mais informações, consulte [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 No prompt de comando, digite o seguinte:  
  
## <a name="syntax"></a>Sintaxe  
  
```  
gacutil [options] [assemblyName | assemblyPath | assemblyListFile]  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Argumento|Descrição|  
|--------------|-----------------|  
|*assemblyName*|O nome de um assembly. É possível fornecer um nome de assembly especificado parcialmente como, por exemplo, `myAssembly` ou um nome de assembly totalmente especificado como, por exemplo, `myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5`.|  
|*assemblyPath*|O nome de um arquivo que contém um manifesto de assembly.|  
|*assemblyListFile*|O caminho para um arquivo de texto ANSI que lista assemblies para instalação ou desinstalação. Para usar um arquivo de texto para instalar assemblies, especifique o caminho para cada assembly em uma linha separada no arquivo. A ferramenta interpreta caminhos relativos em relação ao local do *assemblyListFile*. Para usar um arquivo de texto para desinstalar assemblies, especifique o nome de assembly totalmente qualificado para cada assembly em uma linha separada no arquivo. Consulte os exemplos de conteúdo *assemblyListFile* adiante neste tópico.|  
  
|Opção|Descrição|  
|------------|-----------------|  
|**/cdl**|Exclui o conteúdo do cache de download.|  
|**/f**|Especifique essa opção com as opções **/i** ou **/il** para forçar a reinstalação de um assembly. Se um assembly com o mesmo nome já estiver no cache de assembly global, a ferramenta o substituirá.|  
|**/h**[**elp**]|Exibe sintaxe de comando e opções para a ferramenta.|  
|**/i** *assemblyPath*|Instala um assembly no cache de assembly global.|  
|**/if**  *assemblyPath*|Instala um assembly no cache de assembly global. Se um assembly com o mesmo nome já estiver no cache de assembly global, a ferramenta o substituirá.<br /><br /> Especificar essa opção equivale a definir as opções **/i** e **/f** juntas.|  
|**/il** *assemblyListFile*|Instala um ou mais assemblies especificados em *assemblyListFile* no cache de assembly global.|  
|**/ir**  *assemblyPath*<br /><br /> *scheme*<br /><br /> *id*<br /><br /> *description*|Instala um assembly no cache de assembly global e adiciona uma referência para contar o assembly. Você deve especificar os parâmetros *assemblyPath*, *scheme*, *id* e *description* com essa opção. Para obter uma descrição dos valores válidos que podem ser especificados nesses parâmetros, consulte a opção **/r**.<br /><br /> Especificar essa opção equivale a definir as opções **/i** e **/r** juntas.|  
|**/l** [*assemblyName*]|Lista o conteúdo do cache de assembly global. Se você especificar o parâmetro *assemblyName*, a ferramenta listará apenas os assemblies que correspondem a esse nome.|  
|**/ldl**|Lista o conteúdo do cache de arquivos baixados.|  
|**/lr** [*assemblyName*]|Lista todos os assemblies e suas contagens de referência correspondentes. Se você especificar o parâmetro *assemblyName*, a ferramenta listará apenas os assemblies que correspondem a esse nome e suas contagens de referência correspondentes.|  
|**/nologo**|Suprime a exibição do banner de inicialização da Microsoft.|  
|**/r** [*assemblyName &#124; assemblyPath*]<br /><br /> *scheme*<br /><br /> *id*<br /><br /> *description*|Especifica uma referência rastreada para um assembly ou assemblies para instalação ou desinstalação. Especifique essa opção com as opções **/i**, **/il**, **/u** ou **/ul**.<br /><br /> Para instalar um assembly, especifique os parâmetros *assemblyPath*, *scheme*, *id* e *description* com essa opção. Para desinstalar um assembly, especifique os parâmetros *assemblyName*, *scheme*, *id* e *description*.<br /><br /> Para remover uma referência a um assembly, você deve especificar os mesmos parâmetros *scheme*, *id* e *description* que foram especificados com as opções **/i** e **/r** (ou **/ir**) quando o assembly foi instalado. Se você estiver desinstalando um assembly, a ferramenta também removerá o assembly do cache de assembly global se for a última referência a ser removida e se o Windows Installer não tiver referências pendentes para o assembly.<br /><br /> O parâmetro *scheme* especifica o tipo de esquema de instalação. É possível especificar um dos seguintes valores:<br /><br /> -   UNINSTALL_KEY: especifique esse valor se o instalador adicionar o aplicativo a Adicionar/Remover Programas no Microsoft Windows. Os aplicativos se adicionam a Adicionar/Remover Programas incluindo uma chave do Registro a HKLM\Software\Microsoft\Windows\CurrentVersion.<br />-   FILEPATH: especifique esse valor se o instalador não adicionar o aplicativo a Adicionar/Remover Programas.<br />-   OPAQUE: especifique esse valor se você estiver fornecendo uma chave do Registro ou um caminho de arquivo não se aplicar ao cenário de instalação. Esse valor permite especificar informações personalizadas para o parâmetro *id*.<br /><br /> O valor a ser especificado para o parâmetro *id* depende do valor especificado para o parâmetro *scheme*:<br /><br /> -   Se você especificar UNINSTALL_KEY para o parâmetro *scheme*, especifique o nome do aplicativo definido na chave do Registro HKLM\Software\Microsoft\Windows\CurrentVersion. Por exemplo, se a chave do Registro for HKLM\Software\Microsoft\Windows\CurrentVersion\MyApp, especifique MyApp para o parâmetro *id*.<br />-   Se você especificar FILEPATH para o parâmetro *scheme*, especifique o caminho completo para o arquivo executável que instala o assembly como o parâmetro *id*.<br />-   Se especificar OPAQUE para o parâmetro *scheme*, você poderá fornecer qualquer dado como o parâmetro *id*. Os dados especificados devem estar entre aspas ("").<br /><br /> O parâmetro *description* permite especificar o texto descritivo sobre o aplicativo a ser instalado. Essas informações são exibidas quando as referências são enumeradas.|  
|**/silent**|Suprime a exibição de toda a saída.|  
|**/u**  *assemblyName*|Desinstala um assembly do cache de assembly global.|  
|**/uf**  *assemblyName*|Força um assembly especificado para desinstalar removendo-se todas as referências para o assembly.<br /><br /> Especificar essa opção equivale a definir as opções **/u** e **/f** juntas. **Observação**: não é possível usar essa opção para remover um assembly que foi instalado usando o Microsoft Windows Installer. Se você tentar essa operação, a ferramenta exibirá uma mensagem de erro.|  
|**/ul** *assemblyListFile*|Desinstala um ou mais assemblies especificados em *assemblyListFile* do cache de assembly global.|  
|**/u**[**ngen**] *assemblyName*|Desinstala um assembly especificado do cache de assembly global. Se o assembly especificado tiver contagens de referência existentes, a ferramenta exibirá as contagens de referência e não removerá o assembly do cache de assembly global. **Observação:** no .NET Framework versão 2.0, não há suporte para `/ungen`. Em vez disso, use o comando `uninstall` do [Ngen.exe (Gerador de Imagens Nativas)](../../../docs/framework/tools/ngen-exe-native-image-generator.md). <br /><br /> No .NET Framework versões 1.0 e 1.1, especificar **/ungen** faz Gacutil.exe remover o assembly do cache de imagens nativas. Esse cache armazena as imagens nativas para assemblies que foram criados usando o [Ngen.exe (Gerador de Imagens Nativas)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).|  
|**/ur**  *assemblyName*<br /><br /> *scheme*<br /><br /> *id*<br /><br /> *description*|Desinstala uma referência de um assembly especificado do cache de assembly global. Para remover uma referência a um assembly, você deve especificar os mesmos parâmetros *scheme*, *id* e *description* que foram especificados com as opções **/i** e **/r** (ou **/ir)** quando o assembly foi instalado. Para obter uma descrição dos valores válidos que podem ser especificados nesses parâmetros, consulte a opção **/r**.<br /><br /> Especificar essa opção equivale a definir as opções **/u** e **/r** juntas.|  
|**/?**|Exibe sintaxe de comando e opções para a ferramenta.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Você deve ter privilégios de administrador para usar Gacutil.exe.  
  
 Mais especificamente, Gacutil.exe permite instalar assemblies no cache, removê-los de cache e listar o conteúdo do cache.  
  
 Gacutil.exe oferece opções que dão suporte à contagem de referências semelhante ao esquema da contagem de referências compatível com o Windows Installer. É possível usar Gacutil.exe para instalar dois aplicativos que instalam o mesmo assembly; a ferramenta acompanha o número de referências para o assembly. Assim, o assembly permanecerá no computador até ambos os aplicativos serem desinstalados. Se você estiver usando Gacutil.exe em instalações de produto reais, use as opções que dão suporte à contagem de referências. Use as opções **/i** e **/r** juntas para instalar um assembly e adicionar uma referência para contá-lo. Use as opções **/u** e **/r** juntas para remover uma contagem de referência para um assembly. Lembre que o uso das opções **/i** e **/u** sozinhas não dá suporte à contagem de referência. Essas opções são apropriadas ao uso durante o desenvolvimento de produtos, mas não para instalações de produto reais.  
  
 Use as opções **/il** ou **/ul** para instalar ou desinstalar uma lista de assemblies armazenadas em um arquivo de texto ANSI. O conteúdo do arquivo de texto deve ser formatado corretamente. Para usar um arquivo de texto para instalar assemblies, especifique o caminho para cada assembly em uma linha separada no arquivo. O exemplo a seguir demonstra o conteúdo de um arquivo que contém assemblies para instalação.  
  
```  
myAssembly1.dll  
myAssembly2.dll  
myAssembly3.dll  
```  
  
 Para usar um arquivo de texto para desinstalar assemblies, especifique o nome de assembly totalmente qualificado para cada assembly em uma linha separada no arquivo. O exemplo a seguir demonstra o conteúdo de um arquivo que contém assemblies para desinstalação.  
  
```  
myAssembly1,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab  
myAssembly2,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab  
myAssembly3,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab  
```  
  
## <a name="examples"></a>Exemplos  
 O comando a seguir instala o assembly `mydll.dll` no cache de assembly global.  
  
```  
gacutil /i mydll.dll  
```  
  
 O comando a seguir remove o assembly `hello` do cache de assembly global, desde que não haja contagens de referência para o assembly.  
  
```  
gacutil /u hello  
```  
  
 O comando anterior pode remover mais de um assembly do cache de assembly porque o nome do assembly não está totalmente especificado. Por exemplo, se as versões 1.0.0.0 e 3.2.2.1 de `hello` forem instaladas no cache, o comando `gacutil /u hello` removerá os assemblies.  
  
 Use o exemplo a seguir para evitar a remoção de mais de um assembly. Esse comando remove apenas o assembly `hello` correspondente ao número de versão totalmente especificado, à cultura e à chave pública.  
  
```  
gacutil /u hello, Version=1.0.0.1, Culture="de",PublicKeyToken=45e343aae32233ca  
```  
  
 O comando a seguir instala os assemblies especificados no arquivo `assemblyList.txt` no cache de assembly global.  
  
 `gacutil /il assemblyList.txt`  
  
 O comando a seguir remove os assemblies especificados no arquivo `assemblyList.txt` do cache de assembly global.  
  
 `gacutil /ul assemblyList.txt`  
  
 O comando a seguir instala `myDll.dll` no cache de assembly global e adiciona uma referência para contá-lo. O assembly `myDll.dll` é usado pelo aplicativo `MyApp`. O parâmetro `UNINSTALL_KEY MyApp` especifica a chave do Registro que adiciona `MyApp` a Adicionar/Remover Programas no Windows. O parâmetro de descrição é especificado como `My Application Description`.  
  
```  
gacutil /i /r myDll.dll UNINSTALL_KEY MyApp "My Application Description"  
```  
  
 O comando a seguir instala `myDll.dll` no cache de assembly global e adiciona uma referência para contá-lo. O parâmetro de esquema, `FILEPATH` e o parâmetro de ID, `c:\applications\myApp\myApp.exe`, especificam o caminho para o aplicativo que está instalando `myDll.dll.`. O parâmetro de descrição é especificado como `MyApp`.  
  
 `gacutil /i /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp`  
  
 O comando a seguir instala `myDll.dll` no cache de assembly global e adiciona uma referência para contá-lo. O parâmetro de esquema, `OPAQUE`, permite personalizar os parâmetros de ID e descrição.  
  
```  
gacutil /i /r mydll.dll OPAQUE "Insert custom application details here" "Insert Custom description information here"  
```  
  
 O comando a seguir remove a referência para `myDll.dll` pelo aplicativo `myApp`. Se essa for a última referência para o assembly, ela também removerá o assembly do cache de assembly global.  
  
 `gacutil /u /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp`  
  
 O comando a seguir lista o conteúdo do cache de assembly global.  
  
```  
gacutil /l  
```  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas](../../../docs/framework/tools/index.md)   
 [Cache de assembly global](../../../docs/framework/app-domains/gac.md)   
 [Regasm.exe (Ferramenta de Registro de Assembly)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)   
 [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

