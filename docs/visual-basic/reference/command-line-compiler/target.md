---
title: /target (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 900693ac3793fb59133b31d8fc0136df63c11a10
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="target-visual-basic"></a>/target (Visual Basic)
Especifica o formato de saída do compilador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/target:{exe | library | module | winexe | appcontainerexe | winmdobj}  
```  
  
## <a name="remarks"></a>Comentários  
 A tabela a seguir resume o efeito do `/target` opção.  
  
|**Opção**|**Comportamento**|  
|----------------|------------------|  
|`/target:exe`|Faz com que o compilador criar um aplicativo de console executável.<br /><br /> Essa é a opção padrão quando nenhum `/target` opção é especificada. O arquivo executável é criado com uma extensão de .exe.<br /><br /> A menos que especificado de outra forma com o `/out` opção, o nome do arquivo de saída usa o nome do arquivo de entrada que contém o `Sub Main` procedimento.<br /><br /> Apenas uma `Sub Main` procedimento é necessário nos arquivos de código-fonte que são compilados em um arquivo .exe. Use o `/main` opção de compilador para especificar a classe que contém o `Sub Main` procedimento.|  
|`/target:library`|Faz com que o compilador para criar uma biblioteca de vínculo dinâmico (DLL).<br /><br /> O arquivo de biblioteca de vínculo dinâmico é criado com uma extensão. dll.<br /><br /> A menos que especificado de outra forma com o `/out` opção, o nome do arquivo de saída usa o nome do arquivo de entrada primeiro.<br /><br /> Ao criar uma DLL, uma `Sub Main` procedimento não é necessário.|  
|`/target:module`|Faz com que o compilador gere um módulo que pode ser adicionado a um assembly.<br /><br /> O arquivo de saída é criado com a extensão. netmodule.<br /><br /> O .NET common language runtime não é possível carregar um arquivo que não tem um assembly. No entanto, você pode incorporar um arquivo no manifesto do assembly de um assembly usando `/reference`.<br /><br /> Quando o código em um módulo faz referência a tipos internos em outro módulo, ambos os módulos devem ser incorporados a um manifesto do assembly usando `/reference`.<br /><br /> O [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) opção importa os metadados de um módulo.|  
|`/target:winexe`|Faz com que o compilador para criar um aplicativo executável do Windows.<br /><br /> O arquivo executável é criado com uma extensão de .exe. Um aplicativo baseado no Windows é aquele que fornece uma interface de usuário da [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] biblioteca de classes ou com as APIs do Win32.<br /><br /> A menos que especificado de outra forma com o `/out` opção, o nome do arquivo de saída usa o nome do arquivo de entrada que contém o `Sub Main` procedimento.<br /><br /> Apenas uma `Sub Main` procedimento é necessário nos arquivos de código-fonte que são compilados em um arquivo .exe. Em casos em que o seu código tem mais de uma classe que tem um `Sub Main` procedimento, use o `/main` opção de compilador para especificar a classe que contém o `Sub Main` procedimento|  
|`/target:appcontainerexe`|Faz com que o compilador criar um aplicativo executável baseados no Windows que deve ser executado em um contêiner do aplicativo. Esta configuração é projetada para ser usado para [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplicativos.<br /><br /> O **appcontainerexe** configuração define um bit no campo de características de [executável portátil](http://go.microsoft.com/fwlink/p/?LinkId=236960) arquivo. Esse bit indica que o aplicativo deve ser executado em um contêiner do aplicativo. Quando esse bit é definido, ocorrerá um erro se o `CreateProcess` método tenta iniciar o aplicativo de fora de um contêiner do aplicativo. Além de essa opção, bit **/target: appcontainerexe** é equivalente a **/target: winexe**.<br /><br /> O arquivo executável é criado com uma extensão de .exe.<br /><br /> A menos que você especifique de outra forma, usando o `/out` opção, o nome do arquivo de saída usa o nome do arquivo de entrada que contém o `Sub Main` procedimento.<br /><br /> Apenas uma `Sub Main` procedimento é necessário nos arquivos de código-fonte que são compilados em um arquivo .exe. Se o seu código contém mais de uma classe que tem um `Sub Main` procedimento, use o `/main` opção de compilador para especificar a classe que contém o `Sub Main` procedimento|  
|`/target:winmdobj`|Faz com que o compilador para criar um arquivo intermediário que possa ser convertido em um arquivo binário (. winmd) de tempo de execução do Windows. O arquivo. winmd pode ser consumido por programas JavaScript e C++, além de programas de linguagem gerenciada.<br /><br /> O arquivo intermediário é criado com uma extensão de .winmdobj.<br /><br /> A menos que você especifique de outra forma, usando o `/out` opção, o nome do arquivo de saída usa o nome do arquivo de entrada primeiro. Um `Sub Main` procedimento não é necessário.<br /><br /> O arquivo .winmdobj foi projetado para ser usado como entrada para o <xref:Microsoft.Build.Tasks.WinMDExp> exportar da ferramenta para produzir um arquivo de metadados (WinMD) do Windows. O arquivo de WinMD tem uma extensão. winmd e contém o código de biblioteca original e as definições de WinMD que JavaScript, C++ e o uso de tempo de execução do Windows.|  
  
 A menos que você especifique `/target:module`, `/target` faz com que um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] manifesto do assembly a ser adicionado a um arquivo de saída.  
  
 Cada instância do Vbc.exe produz, no máximo, um arquivo de saída. Se você especificar uma opção de compilador como `/out` ou `/target` mais de uma vez, o último deles é que o compilador processa entrem em vigor. Informações sobre todos os arquivos em uma compilação são adicionadas ao manifesto. Todos os arquivos, exceto aqueles criados com de saída `/target:module` conter metadados do assembly no manifesto. Use [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1) para exibir os metadados em um arquivo de saída.  
  
 A forma abreviada de `/target` é `/t`.  
  
### <a name="to-set-target-in-the-visual-studio-ide"></a>Para definir /target no IDE do Visual Studio  
  
1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**.   
  
2.  Clique na guia **Aplicativo**.  
  
3.  Modificar o valor de **tipo de aplicativo** caixa.  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `in.vb`, criar `in.dll`:  
  
```  
vbc /target:library in.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/main](../../../visual-basic/reference/command-line-compiler/main.md)  
 [entrada/saída (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)  
 [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [/moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)  
 [Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
