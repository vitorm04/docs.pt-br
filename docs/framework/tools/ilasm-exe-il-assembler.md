---
title: Ilasm.exe (IL Assembler)
ms.date: 03/30/2017
helpviewer_keywords:
- MSIL generators
- metadata, MSIL Assembler
- MSIL Assembler
- portable executable files, MSIL Assembler
- PE files, MSIL Assembler
- MSIL
- Ilasm.exe
- verifying MSIL performance
ms.assetid: 4ca3a4f0-4400-47ce-8936-8e219961c76f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36de7dd2d97eb532717d52bd3903d3e5acd19d2d
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567058"
---
# <a name="ilasmexe-il-assembler"></a>Ilasm.exe (IL Assembler)

O IL Assembler gera um arquivo PE (Portable Executable) com base em IL (Intermediate Language). (Para obter mais informações sobre IL, consulte [Processo de execução gerenciada](../../../docs/standard/managed-execution-process.md).) É possível executar o executável resultante, que contém IL e os metadados obrigatórios, para determinar se a IL é executada conforme esperado.

Essa ferramenta é instalada automaticamente com o Visual Studio. Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor para Visual Studio (ou o Prompt de Comando do Visual Studio no Windows 7). Para obter mais informações, consulte [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

No prompt de comando, digite o seguinte:

## <a name="syntax"></a>Sintaxe

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a>Parâmetros

| Argumento | DESCRIÇÃO |
| -------- | ----------- |
|`filename`|O nome do arquivo de origem .il. Esse arquivo consiste em diretivas de declaração de metadados e instruções de IL simbólicas. Vários argumentos do arquivo de origem podem ser fornecidos para produzir um único arquivo PE com *Ilasm.exe*. **Observação:** Verifique se a última linha do código no arquivo de origem .il tem espaço em branco à direita ou um caractere de final de linha.|

| Opção | DESCRIÇÃO |
| ------ | ----------- |
|**/32bitpreferred**|Cria uma imagem preferida de 32 bits (PE32).|
|**/alignment:** `integer`|Define FileAlignment como o valor especificado por `integer` no cabeçalho Opcional do NT. Se a diretiva IL .alignment for especificada no arquivo, essa opção a substituirá.|
|**/appcontainer**|Produz um arquivo *.dll* ou *.exe* que é executado no contêiner do aplicativo do Windows, como saída.|
|**/arm**|Especifica o ARM (Advanced RISC Machine) como o processador de destino.<br /><br /> Se nenhum número de bit da imagem for especificado, o padrão será **/32bitpreferred**.|
|**/base:** `integer`|Define ImageBase como o valor especificado por `integer` no cabeçalho Opcional do NT. Se a diretiva IL .imagebase for especificada no arquivo, essa opção a substituirá.|
|**/clock**|Mede e relata os seguintes tempos de compilação em milissegundos para o arquivo de origem .il especificado:<br /><br /> **Total de execução**: o tempo total gasto na realização de todas as operações específicas que seguem.<br /><br /> **Inicialização**: carregar e abrir o arquivo.<br /><br /> **Emitir MD**: emitir metadados.<br /><br /> **Resolução de referência para definição**: resolver referências para definições no arquivo.<br /><br /> **Geração do arquivo CEE**: gerar a imagem do arquivo na memória.<br /><br /> **Gravação do arquivo PE**: gravação da imagem em um arquivo PE.|
|**/debug**[:**IMPL**&#124;**OPT**]|Inclui informações de depuração (variável local e nomes de argumento, além de números da linha). Cria um arquivo PDB.<br /><br /> **/debug** sem valor adicional desabilita a otimização JIT e usa pontos de sequência do arquivo PDB.<br /><br /> **IMPL** desabilita a otimização JIT e usa pontos de sequência implícitos.<br /><br /> **OPT** habilita a otimização JIT e usa pontos de sequência implícitos.|
|**/dll**|Produz um arquivo *.dll* como saída.|
|**/enc:** `file`|Cria deltas Editar e Continuar com base no arquivo de origem especificado.<br /><br /> Este argumento se destina apenas ao uso acadêmico e não é compatível com uso comercial.|
|**/exe**|Produz um arquivo executável como saída. Esse é o padrão.|
|**/flags:** `integer`|Define ImageFlags como o valor especificado por `integer` no cabeçalho do Common Language Runtime. Se a diretiva IL .corflags for especificada no arquivo, essa opção a substituirá. Consulte CorHdr.h, COMIMAGE_FLAGS para obter uma lista de valores válidos para *integer*.|
|**/fold**|Dobra corpos de método idênticos em um.|
|/**highentropyva**|Produz um executável de saída que dá suporte a ASLR (Address Space Layout Randomization) de alta entropia. (Padrão para **/appcontainer**.)|
|**/include:** `includePath`|Define um caminho para procurar arquivos incluídos com `#include`.|
|**/itanium**|Especifica Intel Itanium como o processador de destino.<br /><br /> Se nenhum número de bit da imagem for especificado, o padrão será **/pe64**.|
|**/key:** `keyFile`|Compila `filename` com uma assinatura forte usando a chave privada contida em `keyFile`.|
|**/key:**  @`keySource`|Compila `filename` com uma assinatura forte usando a chave privada produzida em `keySource`.|
|**/listing**|Produz um arquivo de listagem na saída padrão. Se você omitir essa opção, nenhum arquivo de listagem será produzido.<br /><br /> Esse parâmetro não é compatível no .NET Framework 2.0 ou posterior.|
|**/mdv:** `versionString`|Defina a cadeia de caracteres de versão dos metadados.|
|**/msv:** `major`.`minor`|Define a versão do fluxo de metadados, em que `major` e `minor` sejam inteiros.|
|**/noautoinherit**|Desabilita a herança padrão de <xref:System.Object> quando nenhuma classe de base está especificada.|
|**/nocorstub**|Suprime a geração do stub CORExeMain.|
|**/nologo**|Suprime a exibição do banner de inicialização da Microsoft.|
|**/output:** `file.ext`|Especifica o nome e a extensão do arquivo de saída. Por padrão, o nome do arquivo de saída é igual ao nome do primeiro arquivo de origem. A extensão padrão é *.exe*. Se você especificar a opção **/dll**, a extensão padrão será *.dll*. **Observação:** a especificação de **/output:** myfile.dll não define a opção **/dll**. Se você não especificar **/dll**, o resultado será um arquivo executável chamado *myfile.dll*.|
|**/optimize**|Otimiza instruções longas para curtas. Por exemplo, `br` para `br.s`.|
|**/pe64**|Cria uma imagem de 64 bits (PE32+).<br /><br /> Se nenhum processador de destino for especificado, o padrão será `/itanium`.|
|**/pdb**|Cria um arquivo PDB sem habilitar o acompanhamento das informações de depuração.|
|**/quiet**|Especifica o modo silencioso; não relata o andamento do assembly.|
|**/resource:** `file.res`|Inclui o arquivo de recurso especificado no formato \*.res no arquivo *.exe* ou *.dll* resultante. Apenas um arquivo .res pode ser especificado com a opção **/resource**.|
|**/ssver:** `int`.`int`|Define o número de versão do subsistema no cabeçalho opcional do NT. Para **/appcontainer** e **/arm** o número de versão mínimo é 6.02.|
|**/stack:** `stackSize`|Define o valor SizeOfStackReserve no cabeçalho Opcional do NT como `stackSize`.|
|**/stripreloc**|Especifica que nenhuma realocação de base é necessária.|
|**/subsystem:** `integer`|Define o subsistema com o valor especificado por `integer` no cabeçalho Opcional do NT. Se a diretiva IL .subsystem for especificada no arquivo, esse comando a substituirá. Consulte winnt.h, IMAGE_SUBSYSTEM para obter uma lista de valores válidos para `integer`.|
|**/x64**|Especifica um processador AMD 64 bits como o processador de destino.<br /><br /> Se nenhum número de bit da imagem for especificado, o padrão será **/pe64**.|
|**/?**|Exibe sintaxe de comando e opções para a ferramenta.|

> [!NOTE]
> Todas as opções para *Ilasm.exe* não diferenciam maiúsculas de minúsculas e são reconhecidas pelas três primeiras letras. Por exemplo, **/lis** equivale a **/listing** e **/res**:myresfile.res equivale a **/resource**:myresfile.res. As opções que especificam argumentos aceitam dois-pontos (:) ou um sinal de igualdade (=) como o separador entre a opção e o argumento. Por exemplo, **/output**:*file.ext* é equivalente a **/output**=*file.ext*.

## <a name="remarks"></a>Comentários

O IL Assembler ajuda fornecedores da ferramentas na criação e na implementação dos geradores IL. Usando *Ilasm.exe*, os desenvolvedores de ferramenta e compilador podem concentrar-se na geração de IL e de metadados sem se preocupar em emitir IL no formato de arquivo PE.

Semelhante a outros compiladores que têm o tempo de execução como destino, por exemplo, C# e Visual Basic, o *Ilasm.exe* não produz arquivos de objeto intermediários e não exige um estágio de vinculação para formar um arquivo PE.

O IL Assembler pode expressar todos os metadados existentes e recursos IL das linguagens de programação com o tempo de execução como destino. Isso permite que o código gerenciado escrito em qualquer uma das linguagens de programação seja expresso adequadamente no IL Assembler e compilado com *Ilasm.exe*.

> [!NOTE]
> A compilação poderá falhar se a última linha do código no arquivo de origem .il não tiver espaço em branco à direita ou um caractere de final de linha.

Você pode usar *Ilasm.exe* junto com sua ferramenta complementar, o [*Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md). O *Ildasm.exe* usa um arquivo PE que contém o código IL e cria um arquivo de texto adequado como entrada para *Ilasm.exe*. Isso é útil, por exemplo, durante a compilação do código em uma linguagem de programação que não dá suporte a todos os atributos de metadados do tempo de execução. Depois de compilar o código e executar a saída por meio do *Ildasm.exe*, o arquivo de texto IL resultante poderá ser editado manualmente para adicionar os atributos ausentes. Em seguida, é possível executar esse arquivo de texto por meio do *Ilasm.exe* para produzir um arquivo executável final.

Também é possível usar essa técnica para produzir um único arquivo PE com base em vários arquivos PE gerados originalmente por compiladores diferentes.

> [!NOTE]
> Atualmente, não é possível usar essa técnica com arquivos PE que contenham código nativo inserido (por exemplo, arquivos PE produzidos por Visual C++).

Para que esse uso combinado de *Ildasm.exe* e *Ilasm.exe* fique o mais preciso possível, por padrão, o assembler não substitui codificações curtas pelas longas que você talvez tenha gravado nas fontes IL (ou que possam ter sido emitidas por outro compilador). Use a opção **/optimize** para substituir codificações curtas sempre que possível.

> [!NOTE]
> O *Ildasm.exe* funciona apenas em arquivos no disco. Ele não funciona em arquivos instalados no cache de assembly global.

Saiba mais sobre a gramática de IL no arquivo asmparse.grammar no SDK do Windows.

## <a name="version-information"></a>Informações de versão

Do .NET Framework 4.5 em diante, é possível anexar um atributo personalizado a uma implementação da interface usando-se código semelhante ao seguinte:

```
.class interface public abstract auto ansi IMyInterface
{
  .method public hidebysig newslot abstract virtual
    instance int32 method1() cil managed
  {
  } // end of method IMyInterface::method1
} // end of class IMyInterface
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

Do .NET Framework 4.5 em diante, é possível especificar um BLOB (objeto binário grande) marshaling arbitrário usando-se sua representação binária bruta, conforme mostrado no seguinte código:

```
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

Saiba mais sobre a gramática de IL no arquivo asmparse.grammar no SDK do Windows.

## <a name="examples"></a>Exemplos

O comando a seguir monta o arquivo IL *myTestFile.il* e produz o executável *myTestFile.exe*.

```console
ilasm myTestFile
```

O comando a seguir monta o arquivo IL *myTestFile.il* e produz o arquivo *.dll* *myTestFile.dll*.

```console
ilasm myTestFile /dll
```

O comando a seguir monta o arquivo IL *myTestFile.il* e produz o *.dll* arquivo *myNewTestFile.dll*.

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

O exemplo de código a seguir mostra um aplicativo extremamente simples que exibe "Hello World!" no console. Você pode compilar seu código e, em seguida, usar a ferramenta [*Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) para gerar um arquivo IL.

```csharp
using System;

public class Hello
{
    public static void Main(String[] args)
    {
        Console.WriteLine("Hello World!");
    }
}
```

O exemplo de código IL a seguir corresponde ao exemplo de código do C# anterior. É possível compilar esse código em um assembly usando a ferramenta IL Assembler. Os exemplos de código IL e do C# exibem "Hello World!" no console.

```
// Metadata version: v2.0.50215
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 2:0:0:0
}
.assembly sample
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module sample.exe
// MVID: {A224F460-A049-4A03-9E71-80A36DBBBCD3}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x02F20000

// =============== CLASS MEMBERS DECLARATION ===================

.class public auto ansi beforefieldinit Hello
       extends [mscorlib]System.Object
{
  .method public hidebysig static void  Main(string[] args) cil managed
  {
    .entrypoint
    // Code size       13 (0xd)
    .maxstack  8
    IL_0000:  nop
    IL_0001:  ldstr      "Hello World!"
    IL_0006:  call       void [mscorlib]System.Console::WriteLine(string)
    IL_000b:  nop
    IL_000c:  ret
  } // end of method Hello::Main

  .method public hidebysig specialname rtspecialname
          instance void  .ctor() cil managed
  {
    // Code size       7 (0x7)
    .maxstack  8
    IL_0000:  ldarg.0
    IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
    IL_0006:  ret
  } // end of method Hello::.ctor

} // end of class Hello
```

## <a name="see-also"></a>Consulte também

- [Ferramentas](../../../docs/framework/tools/index.md)
- [*Ildasm.exe* (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
- [Processo de execução gerenciada](../../../docs/standard/managed-execution-process.md)
- [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
