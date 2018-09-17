---
title: -target (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e3f691da48db863edd20bc6881785940a5451ef
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45750045"
---
# <a name="-target-visual-basic"></a>-target (Visual Basic)
Especifica o formato da saída do compilador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-target:{exe | library | module | winexe | appcontainerexe | winmdobj}  
```  
  
## <a name="remarks"></a>Comentários  
 A tabela a seguir resume o efeito do `-target` opção.  
  
|**Opção**|**Comportamento**|  
|----------------|------------------|  
|`-target:exe`|Faz com que o compilador crie um aplicativo de console executável.<br /><br /> Essa é a opção padrão quando nenhum `-target` opção for especificada. O arquivo executável é criado com uma extensão de .exe.<br /><br /> A menos que especificado de outra forma com o `/out` opção, o nome do arquivo de saída usa o nome do arquivo de entrada que contém o `Sub Main` procedimento.<br /><br /> Apenas uma `Sub Main` procedimento é necessário nos arquivos de código-fonte que são compilados em um arquivo .exe. Use o `-main` opção de compilador para especificar qual classe contém o `Sub Main` procedimento.|  
|`-target:library`|Faz com que o compilador crie uma biblioteca de vínculo dinâmico (DLL).<br /><br /> O arquivo de biblioteca de vínculo dinâmico é criado com uma extensão. dll.<br /><br /> A menos que especificado de outra forma com o `-out` opção, o nome do arquivo de saída leva o nome do primeiro arquivo de entrada.<br /><br /> Ao criar uma DLL, um `Sub Main` procedimento não é necessário.|  
|`-target:module`|Faz com que o compilador gere um módulo que pode ser adicionado a um assembly.<br /><br /> O arquivo de saída é criado com uma extensão. netmodule.<br /><br /> O .NET common language runtime não é possível carregar um arquivo que não tem um assembly. No entanto, você pode incorporar um arquivo desse tipo no manifesto do assembly de um assembly usando `-reference`.<br /><br /> Quando o código em um módulo fizer referência a tipos internos em outro módulo, ambos os módulos deverão ser incorporados em um manifesto do assembly usando `-reference`.<br /><br /> O [- addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) opção importa os metadados de um módulo.|  
|`-target:winexe`|Faz com que o compilador crie um aplicativo executável com base em Windows.<br /><br /> O arquivo executável é criado com uma extensão de .exe. Um aplicativo baseado no Windows é aquele que fornece uma interface do usuário de qualquer um de [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] biblioteca de classes ou com as APIs do Win32.<br /><br /> A menos que especificado de outra forma com o `-out` opção, o nome do arquivo de saída usa o nome do arquivo de entrada que contém o `Sub Main` procedimento.<br /><br /> Apenas uma `Sub Main` procedimento é necessário nos arquivos de código-fonte que são compilados em um arquivo .exe. Em casos em que o código tem mais de uma classe que tem um `Sub Main` procedimento, use o `-main` opção de compilador para especificar qual classe contém o `Sub Main` procedimento|  
|`-target:appcontainerexe`|Faz com que o compilador crie um aplicativo baseado em Windows executável que deve ser executado em um contêiner de aplicativo. Esta configuração é projetada para ser usado para [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplicativos.<br /><br /> O **appcontainerexe** configuração define um bit no campo de características a [executável portátil](/windows/desktop/Debug/pe-format) arquivo. Esse bit indica que o aplicativo deve ser executado em um contêiner de aplicativo. Quando esse bit estiver definido, ocorrerá um erro se o `CreateProcess` método tenta iniciar o aplicativo fora de um contêiner de aplicativo. Além de essa definição de bits **-target: appcontainerexe** é equivalente a **-target: winexe**.<br /><br /> O arquivo executável é criado com uma extensão de .exe.<br /><br /> A menos que você especifique de outra forma, usando o `-out` opção, o nome do arquivo de saída usa o nome do arquivo de entrada que contém o `Sub Main` procedimento.<br /><br /> Apenas uma `Sub Main` procedimento é necessário nos arquivos de código-fonte que são compilados em um arquivo .exe. Se seu código contiver mais de uma classe que tem um `Sub Main` procedimento, use o `-main` opção de compilador para especificar qual classe contém o `Sub Main` procedimento|  
|`-target:winmdobj`|Faz com que o compilador crie um arquivo intermediário que pode ser convertido em um arquivo binário (. winmd) de tempo de execução do Windows. O arquivo. winmd pode ser consumido por programas JavaScript e C++, além de programas de linguagem gerenciada.<br /><br /> O arquivo intermediário é criado com uma extensão. winmdobj.<br /><br /> A menos que você especifique de outra forma, usando o `-out` opção, o nome do arquivo de saída leva o nome do primeiro arquivo de entrada. Um `Sub Main` procedimento não é necessário.<br /><br /> O arquivo. winmdobj foi projetado para ser usado como entrada para o <xref:Microsoft.Build.Tasks.WinMDExp> exportar da ferramenta para produzir um arquivo de metadados (WinMD) do Windows. O arquivo WinMD tem uma extensão. winmd e contém o código de biblioteca original e as definições de WinMD pelo JavaScript, C++ e o uso de tempo de execução do Windows.|  
  
 A menos que você especifique `-target:module`, `-target` faz com que um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] manifesto do assembly a ser adicionado a um arquivo de saída.  
  
 Cada instância do Vbc.exe produz, no máximo, um arquivo de saída. Se você especificar uma opção de compilador, como `-out` ou `-target` mais de uma vez, o último deles, o compilador processa é colocado em vigor. Informações sobre todos os arquivos em uma compilação são adicionadas ao manifesto. Todos os arquivos, exceto aqueles criados com de saída `-target:module` contêm metadados no manifesto do assembly. Use [Ildasm.exe (IL Disassembler)](../../../framework/tools/ildasm-exe-il-disassembler.md) para exibir os metadados em um arquivo de saída.  
  
 A forma abreviada de `-target` é `-t`.  
  
### <a name="to-set--target-in-the-visual-studio-ide"></a>Para definir - alvo no IDE do Visual Studio  
  
1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**.   
  
2.  Clique na guia **Aplicativo**.  
  
3.  Modificar o valor de **tipo de aplicativo** caixa.  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `in.vb`, criando `in.dll`:  
  
```console
vbc -target:library in.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)  
- [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)  
- [-referência (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
- [-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)  
- [Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
