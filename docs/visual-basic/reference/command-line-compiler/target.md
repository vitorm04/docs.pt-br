---
title: -Target (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
ms.openlocfilehash: 2d7ccfc6b033a9021e683a4a2501ca2ccc29956d
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004943"
---
# <a name="-target-visual-basic"></a>-Target (Visual Basic)
Especifica o formato da saída do compilador.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-target:{exe | library | module | winexe | appcontainerexe | winmdobj}  
```  
  
## <a name="remarks"></a>Comentários  
 A tabela a seguir resume o efeito da opção `-target`.  
  
|**Opção**|**Comportamento**|  
|----------------|------------------|  
|`-target:exe`|Faz com que o compilador crie um aplicativo de console executável.<br /><br /> Essa é a opção padrão quando nenhuma opção `-target` é especificada. O arquivo executável é criado com uma extensão. exe.<br /><br /> A menos que especificado de outra forma com a opção `/out`, o nome do arquivo de saída usa o nome do arquivo de entrada que contém o procedimento `Sub Main`.<br /><br /> Somente um procedimento `Sub Main` é necessário nos arquivos de código-fonte que são compilados em um arquivo. exe. Use a opção de compilador `-main` para especificar qual classe contém o procedimento `Sub Main`.|  
|`-target:library`|Faz com que o compilador crie uma DLL (biblioteca de vínculo dinâmico).<br /><br /> O arquivo da biblioteca de vínculo dinâmico é criado com uma extensão. dll.<br /><br /> A menos que especificado de outra forma com a opção `-out`, o nome do arquivo de saída usa o nome do primeiro arquivo de entrada.<br /><br /> Ao criar uma DLL, um procedimento `Sub Main` não é necessário.|  
|`-target:module`|Faz com que o compilador gere um módulo que pode ser adicionado a um assembly.<br /><br /> O arquivo de saída é criado com uma extensão de. netmodule.<br /><br /> O .NET Common Language Runtime não pode carregar um arquivo que não tem um assembly. No entanto, você pode incorporar esse arquivo ao manifesto do assembly de um assembly usando `-reference`.<br /><br /> Quando o código em um módulo faz referência a tipos internos em outro módulo, ambos os módulos devem ser incorporados a um manifesto do assembly usando `-reference`.<br /><br /> A opção [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) importa os metadados de um módulo.|  
|`-target:winexe`|Faz com que o compilador crie um aplicativo executável baseado no Windows.<br /><br /> O arquivo executável é criado com uma extensão. exe. Um aplicativo baseado no Windows é aquele que fornece uma interface do usuário da biblioteca de classes .NET Framework ou com as APIs do Windows.<br /><br /> A menos que especificado de outra forma com a opção `-out`, o nome do arquivo de saída usa o nome do arquivo de entrada que contém o procedimento `Sub Main`.<br /><br /> Somente um procedimento `Sub Main` é necessário nos arquivos de código-fonte que são compilados em um arquivo. exe. Nos casos em que seu código tem mais de uma classe que tem um procedimento `Sub Main`, use a opção de compilador `-main` para especificar qual classe contém o procedimento `Sub Main`|  
|`-target:appcontainerexe`|Faz com que o compilador crie um aplicativo executável baseado em Windows que deve ser executado em um contêiner de aplicativo. Essa configuração foi projetada para ser usada para aplicativos [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)].<br /><br /> A configuração **appcontainerexe** define um bit no campo características do arquivo [executável portátil](/windows/desktop/Debug/pe-format) . Esse bit indica que o aplicativo deve ser executado em um contêiner de aplicativo. Quando esse bit for definido, ocorrerá um erro se o método `CreateProcess` tentar iniciar o aplicativo fora de um contêiner de aplicativo. Além dessa configuração de bit, **-target: appcontainerexe** é equivalente a **-target: winexe**.<br /><br /> O arquivo executável é criado com uma extensão. exe.<br /><br /> A menos que você especifique o contrário usando a opção `-out`, o nome do arquivo de saída usa o nome do arquivo de entrada que contém o procedimento `Sub Main`.<br /><br /> Somente um procedimento `Sub Main` é necessário nos arquivos de código-fonte que são compilados em um arquivo. exe. Se o seu código contiver mais de uma classe que tenha um procedimento `Sub Main`, use a opção de compilador `-main` para especificar qual classe contém o procedimento `Sub Main`|  
|`-target:winmdobj`|Faz com que o compilador crie um arquivo intermediário que você pode converter em um arquivo binário Windows Runtime (. winmd). O arquivo. winmd pode ser consumido por C++ JavaScript e programas, além de programas de linguagem gerenciada.<br /><br /> O arquivo intermediário é criado com uma extensão. winmdobj.<br /><br /> A menos que você especifique o contrário usando a opção `-out`, o nome do arquivo de saída usa o nome do primeiro arquivo de entrada. Um procedimento `Sub Main` não é necessário.<br /><br /> O arquivo. winmdobj foi projetado para ser usado como entrada para a ferramenta de exportação <xref:Microsoft.Build.Tasks.WinMDExp> para produzir um arquivo de metadados do Windows (WinMD). O arquivo WinMD tem uma extensão. WinMD e contém o código da biblioteca original e as definições de WinMD que o JavaScript, C++o e o Windows Runtime usam.|  
  
 A menos que você especifique `-target:module`, `-target` fará com que um manifesto de assembly .NET Framework seja adicionado a um arquivo de saída.  
  
 Cada instância do Vbc. exe produz, no máximo, um arquivo de saída. Se você especificar uma opção de compilador como `-out` ou `-target` mais de uma vez, o último que os processos do compilador será colocado em vigor. As informações sobre todos os arquivos em uma compilação são adicionadas ao manifesto. Todos os arquivos de saída, exceto aqueles criados com `-target:module`, contêm metadados de assembly no manifesto. Use [ILDASM. exe (desmontador de Il)](../../../framework/tools/ildasm-exe-il-disassembler.md) para exibir os metadados em um arquivo de saída.  
  
 A forma abreviada de `-target` é `-t`.  
  
### <a name="to-set--target-in-the-visual-studio-ide"></a>Para definir o destino no IDE do Visual Studio  
  
1. Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**.   
  
2. Clique na guia **Aplicativo**.  
  
3. Modifique o valor na caixa **tipo de aplicativo** .  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `in.vb`, criando `in.dll`:  
  
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
- [Assemblies no .NET](../../../standard/assembly/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
