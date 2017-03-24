---
title: /Target (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
caps.latest.revision: 29
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ccdb87188b924303057d5867dccece937defe74d
ms.lasthandoff: 03/13/2017

---
# <a name="target-visual-basic"></a>/target (Visual Basic)
Especifica o formato de saída do compilador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/target:{exe | library | module | winexe | appcontainerexe | winmdobj}  
```  
  
## <a name="remarks"></a>Comentários  
 A tabela a seguir resume o efeito de `/target` opção.  
  
|**Opção**|**Comportamento**|  
|----------------|------------------|  
|`/target:exe`|Faz com que o compilador criar um aplicativo de console executável.<br /><br /> Essa é a opção padrão quando nenhum `/target` opção é especificada. O arquivo executável é criado com a extensão .exe.<br /><br /> A menos que especificado de outra forma com o `/out` opção, o nome do arquivo de saída usa o nome do arquivo de entrada que contém o `Sub Main` procedimento.<br /><br /> Apenas uma `Sub Main` procedimento é necessário nos arquivos de código-fonte que são compilados em um arquivo .exe. Use o `/main` opção de compilador para especificar a classe que contém o `Sub Main` procedimento.|  
|`/target:library`|Faz com que o compilador para criar uma biblioteca de vínculo dinâmico (DLL).<br /><br /> O arquivo de biblioteca de vínculo dinâmico é criado com uma extensão. dll.<br /><br /> A menos que especificado de outra forma com o `/out` opção, o nome do arquivo de saída usa o nome do arquivo de entrada primeiro.<br /><br /> Ao criar uma DLL, uma `Sub Main` procedimento não é necessário.|  
|`/target:module`|Faz com que o compilador gere um módulo que pode ser adicionado a um assembly.<br /><br /> O arquivo de saída é criado com a extensão. netmodule.<br /><br /> O .NET common language runtime não é possível carregar um arquivo que não tem um assembly. No entanto, é possível incorporar um arquivo de manifesto do assembly de um assembly usando `/reference`.<br /><br /> Quando o código em um módulo referencia tipos internos em outro módulo, ambos os módulos devem ser incorporados em um manifesto de assembly usando `/reference`.<br /><br /> O [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) opção importa os metadados de um módulo.|  
|`/target:winexe`|Faz com que o compilador para criar um aplicativo executável do Windows.<br /><br /> O arquivo executável é criado com a extensão .exe. Um aplicativo baseado no Windows é aquele que fornece uma interface de usuário do [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] biblioteca de classes ou com as APIs do Win32.<br /><br /> A menos que especificado de outra forma com o `/out` opção, o nome do arquivo de saída usa o nome do arquivo de entrada que contém o `Sub Main` procedimento.<br /><br /> Apenas uma `Sub Main` procedimento é necessário nos arquivos de código-fonte que são compilados em um arquivo .exe. Em casos onde o código tem mais de uma classe que tem um `Sub Main` procedimento, use o `/main` opção de compilador para especificar a classe que contém o `Sub Main` procedimento|  
|`/target:appcontainerexe`|Faz com que o compilador para criar um aplicativo executável baseados no Windows que deve ser executado em um contêiner de aplicativos. Esta configuração é projetada para ser usado para [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)] aplicativos.<br /><br /> O **appcontainerexe** configuração define um bit no campo de características de [Portable Executable](http://go.microsoft.com/fwlink/p/?LinkId=236960) arquivo. Esse bit indica que o aplicativo deve ser executado em um contêiner de aplicativos. Quando esse bit estiver definido, ocorrerá um erro se o `CreateProcess` método tenta iniciar o aplicativo fora do contêiner do aplicativo. Além de essa configuração, bit **/target: appcontainerexe** é equivalente a **/target: winexe**.<br /><br /> O arquivo executável é criado com a extensão .exe.<br /><br /> A menos que você especifique de outra forma, usando o `/out` opção, o nome do arquivo de saída usa o nome do arquivo de entrada que contém o `Sub Main` procedimento.<br /><br /> Apenas uma `Sub Main` procedimento é necessário nos arquivos de código-fonte que são compilados em um arquivo .exe. Se o seu código contiver mais de uma classe que tem um `Sub Main` procedimento, use o `/main` opção de compilador para especificar a classe que contém o `Sub Main` procedimento|  
|`/target:winmdobj`|Faz com que o compilador para criar um arquivo intermediário que possa ser convertido em um arquivo binário (. winmd) de tempo de execução do Windows. O arquivo. winmd pode ser consumido por programas JavaScript e C++, além de programas de linguagem gerenciada.<br /><br /> O arquivo intermediário é criado com uma extensão. winmdobj.<br /><br /> A menos que você especifique de outra forma, usando o `/out` opção, o nome do arquivo de saída usa o nome do arquivo de entrada primeiro. Um `Sub Main` procedimento não é obrigatório.<br /><br /> O arquivo. winmdobj foi projetado para ser usado como entrada para o <xref:Microsoft.Build.Tasks.WinMDExp>Exportar a ferramenta para produzir um arquivo de metadados (WinMD) do Windows.</xref:Microsoft.Build.Tasks.WinMDExp> O arquivo WinMD tem uma extensão. winmd e contém os dois o código da biblioteca do original e as definições de WinMD que JavaScript, C++ e o uso de tempo de execução do Windows.|  
  
 A menos que você especifique `/target:module`, `/target` faz com que um [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] manifesto do assembly a ser adicionado a um arquivo de saída.  
  
 Cada instância de Vbc.exe produz, no máximo, um arquivo de saída. Se você especificar uma opção de compilador como `/out` ou `/target` mais de uma vez, o último elemento é que o compilador processa entrem em vigor. Informações sobre todos os arquivos em uma compilação são adicionadas ao manifesto. Todos os arquivos, exceto aqueles criados com de saída `/target:module` contêm metadados de assembly do manifesto. Use [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1) para exibir os metadados em um arquivo de saída.  
  
 A forma abreviada do `/target` é `/t`.  
  
### <a name="to-set-target-in-the-visual-studio-ide"></a>Definir /target no IDE do Visual Studio  
  
1.  Tenha um projeto selecionado no **Solution Explorer**. No menu **Projeto**, clique em **Propriedades**. Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Clique o **aplicativo** guia.  
  
3.  Modificar o valor de **tipo de aplicativo** caixa.  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `in.vb`, criar `in.dll`:  
  
```  
vbc /target:library in.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/Main](../../../visual-basic/reference/command-line-compiler/main.md)   
 [entrada/saída (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)   
 [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)   
 [/moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)   
 [Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
