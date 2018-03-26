---
title: Opções do compilador (F#)
description: 'Use opções de linha de comando do compilador F # para controlar a compilação de aplicativos do F # e bibliotecas.'
keywords: visual f#, f#, programação funcional
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c797cf0b-5953-4053-8626-0558e9eaf10f
ms.openlocfilehash: 23731832141bc2f74a04c5f4027fc210b5589537
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2018
---
# <a name="compiler-options"></a>Opção de compilador

Este tópico descreve as opções do compilador de linha de comando para o compilador de F #, fsc.exe. O ambiente de compilação também pode ser controlado pela configuração das propriedades do projeto.


## <a name="compiler-options-listed-alphabetically"></a>Opções do compilador listadas em ordem alfabética
A tabela a seguir mostra as opções do compilador listadas em ordem alfabética. Algumas das opções de compilador F # são semelhantes às opções do compilador c#. Se esse for o caso, é fornecido um link para o tópico de opções do compilador c#.



|Opção de compilador|Descrição|
|---------------|-----------|
|**-a****&lt;output-filename&gt;**|Gera uma biblioteca e especifica seu nome de arquivo. Essa opção é uma forma abreviada de **-target: library *&lt;filename&gt;**.|
|**--baseaddress:&lt;string&gt;**|Especifica o endereço base da biblioteca a ser criada.<br /><br />Essa opção de compilador é equivalente à opção de compilador c# do mesmo nome. Para obter mais informações, consulte [ &#47;baseaddress &#40;C&#35; opções do compilador&#41;](https://msdn.microsoft.com/library/2fdbz5xd.aspx).|
|**--codepage:&lt;int&gt;**|Especifica a página de código usada para ler arquivos de origem.<br /><br />Essa opção de compilador é equivalente à opção de compilador c# do mesmo nome. Para obter mais informações, consulte [ &#47;codepage &#40;C&#35; opções do compilador&#41;](https://msdn.microsoft.com/library/w0kyekyh.aspx).|
|**--consolecolors**|Especifica que erros e avisos usam texto codificado por cores no console.|
|**--crossoptimize**[**+**&#124;**-**]|Habilita ou desabilita otimizações de módulo cruzado.|
|**--delaysign**[**+**&#124;**-**]|Sinais de atraso do assembly usando somente a parte pública da chave de nome forte.<br /><br />Essa opção de compilador é equivalente à opção de compilador c# do mesmo nome. Para obter mais informações, consulte [ &#47;delaysign &#40;C&#35; opções do compilador&#41;](https://msdn.microsoft.com/library/ta1sxwy8.aspx).|
|**--checked**[**+**&#124;**-**]|Habilita ou desabilita a geração de verificações de estouro.<br /><br />Essa opção de compilador é equivalente à opção de compilador c# do mesmo nome. Para obter mais informações, consulte [ &#47;check &#40;C&#35; opções do compilador&#41;](https://msdn.microsoft.com/library/h25wtyxf.aspx).|
|**--debug**[**+**&#124;**-**]<br /><br />**-g**[**+**&#124;**-**]<br /><br />**--debug**:[**full**&#124;**pdbonly**]<br /><br />**-g:** [**full**&#124;**pdbonly**]|Habilita ou desabilita a geração das informações de depuração ou especifica o tipo de informações de depuração para gerar. O padrão é completo, que permite anexar a um programa em execução. Escolha **pdbonly** para obter informações de depuração limitadas armazenadas em um arquivo pdb (banco de dados de programa).<br /><br />Equivalente à opção de compilador c# do mesmo nome. Para saber mais, veja<br /><br />[&#47;Depurar &#40;C&#35; opções do compilador&#41;](https://msdn.microsoft.com/library/8cw0bt21.aspx).|
|**--define:&lt;string&gt;**<br /><br />**-d:&lt;string&gt;**|Define um símbolo para uso na compilação condicional.|
|**--deterministic**[**+**&#124;**-**]|Produza um assembly determinístico (incluindo o GUID da versão do módulo e o carimbo de hora).  Isso não pode ser usado com números de versão de curinga e só dá suporte a tipos de depuração portátil e inseridos|
|**--doc:&lt;xmldoc-filename&gt;**|Instrui o compilador para gerar comentários da documentação XML para o arquivo especificado. Para obter mais informações, consulte [documentação XML](xml-documentation.md).<br /><br />Essa opção de compilador é equivalente à opção de compilador c# do mesmo nome. Para obter mais informações, consulte [ &#47;documento &#40;C&#35; opções do compilador&#41;](https://msdn.microsoft.com/library/3260k4x7.aspx).|
|**--fullpaths**|Instrui o compilador gere caminhos totalmente qualificados.<br /><br />Essa opção de compilador é equivalente à opção de compilador c# do mesmo nome. Para obter mais informações, consulte [ &#47;fullpaths &#40;C&#35; opções do compilador&#41;](https://msdn.microsoft.com/library/d315xc66.aspx).|
|**--help**<br /><br />**-?**|Exibe informações de uso, incluindo uma breve descrição de todas as opções do compilador.|
|**--highentropyva**[**+**&#124;**-**]|Habilitar ou desabilitar o endereço de alta entropia aleatorização do espaço (ASLR), um recurso de segurança aprimorada. O sistema operacional aleatoriamente os locais na memória em que a infraestrutura de aplicativos (como a pilha e heap) é carregada. Se você habilitar essa opção, sistemas operacionais pode usar este aleatória para usar o espaço de endereço de 64 bits de completo em um computador de 64 bits.|
|**--keycontainer:&lt;string&gt;**|Especifica um contêiner de chave de nome forte.|
|**--keyfile:&lt;filename&gt;**|Especifica o nome do arquivo de chave pública para assinar o assembly gerado.|
|**--lib:&lt;folder-name&gt;**<br /><br />**-I:&lt;folder-name&gt;**|Especifica um diretório a ser procurado em assemblies referenciados.<br /><br />Essa opção de compilador é equivalente à opção de compilador c# do mesmo nome. Para obter mais informações, consulte [ &#47;lib &#40;C&#35; opções do compilador&#41;](https://msdn.microsoft.com/library/s5bac5fx.aspx).|
|**--linkresource**:**&lt;resource-info&gt;**|Vincula um recurso especificado para o assembly. O formato de informações de recurso é *filename*[,*nome*[,*pública*&#124;*privada*]]<br /><br />Vincular um recurso único com esta opção é uma alternativa para a incorporação de um arquivo de recursos inteiro com o **– recursos** opção.<br /><br />Essa opção de compilador é equivalente à opção de compilador c# do mesmo nome. Para obter mais informações, consulte [ &#47;linkresource &#40;C&#35; opções do compilador&#41;](https://msdn.microsoft.com/library/xawyf94k.aspx).|
|**--mlcompatibility**|Ignora os avisos que aparecem quando você usa recursos que são projetados para compatibilidade com outras versões do ML.|
|**--noframework**|Desabilita a referência padrão para o assembly do .NET Framework.|
|**--nointerfacedata**|Instrui o compilador para omitir o recurso normalmente adiciona a um assembly que inclui F #-metadados específicos.|
|**--nologo**|Não mostrar o texto da faixa ao iniciar o compilador.|
|**--nooptimizationdata**|Instrui o compilador para incluir apenas otimização essencial para a implementação de construções embutidas. Inibe inlining de módulo cruzado, mas aumenta a compatibilidade binária.|
|**--nowin32manifest**|Instrui o compilador para omitir o manifesto Win32 padrão.|
|**--nowarn:&lt;int-list&gt;**|Desabilita avisos específicos, listados por número. Separe cada número de aviso por uma vírgula. Você pode descobrir o número de aviso para qualquer aviso de saída da compilação.<br /><br />Essa opção de compilador é equivalente à opção de compilador c# do mesmo nome. Para obter mais informações, consulte [ &#47;nowarn &#40;C&#35; opções do compilador&#41;](https://msdn.microsoft.com/library/7f28x9z3.aspx).|
|**--optimize**[**+**&#124;**-**]**[&lt;string-list&gt;]**<br /><br />**-O[+&#124;-] [&lt;string-list&gt;]**|Habilita ou desabilita otimizações. Algumas opções de otimização podem ser desabilitadas ou habilitadas seletivamente listando-os. Esses são: **nojitoptimize**, **nojittracking**, **nolocaloptimize**, **nocrossoptimize**, **notailcalls**.|
|**--out:&lt;output-filename&gt;**<br /><br />**-o:&lt;output-filename&gt;**|Especifica o nome do assembly compilado ou módulo.<br /><br />Essa opção de compilador é equivalente à opção de compilador c# do mesmo nome. Para obter mais informações, consulte [ &#47;out &#40;C&#35; opções do compilador&#41;](https://msdn.microsoft.com/library/bw3t50f3.aspx).|
|**--pdb:&lt;pdb-filename&gt;**|Nomes de arquivo de saída depuração PDB (banco de dados de programa). Essa opção só se aplica quando **– depurar** também está habilitado.<br /><br />Essa opção de compilador é equivalente à opção de compilador c# do mesmo nome. Para obter mais informações, consulte [ &#47;pdb &#40;C&#35; opções do compilador&#41;](https://msdn.microsoft.com/library/ms228625.aspx).|
|**--platform:&lt;platform-name&gt;**|Especifica que o código gerado será executado somente na plataforma especificada (**x86**, **Itanium**, ou **x64**), ou, se o nome da plataforma **anycpu**é escolhida, especifica que o código gerado pode ser executado em qualquer plataforma.<br /><br />Essa opção de compilador é equivalente à opção de compilador c# do mesmo nome. Para obter mais informações, consulte [ &#47;plataforma &#40;C&#35; opções do compilador&#41;](https://msdn.microsoft.com/library/zekwfyz4.aspx).|
|**--preferreduilang:&lt;lang&gt;**| Especifica o nome de cultura de idioma de saída preferencial (por exemplo, es-ES, ja-JP). |
|**--quotations-debug**|Especifica que as informações de depuração extra devem ser emitida para expressões que são derivadas de literais de cotação F # e refletem definições. As informações de depuração são adicionadas para os atributos personalizados de um nó de árvore de expressão F #. Consulte [citações de código](code-quotations.md) e [customattributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**--reference:&lt;assembly-filename&gt;**<br /><br />**-r** &lt;**assembly-filename&gt;**|Disponibiliza código de um assembly F # ou do .NET Framework para o código que está sendo compilado.<br /><br />Essa opção de compilador é equivalente à opção de compilador c# do mesmo nome. Para obter mais informações, consulte [ &#47;referência &#40;C&#35; opções do compilador&#41;](https://msdn.microsoft.com/library/yabyz3h4.aspx).|
|**--resource:&lt;resource-filename&gt;**|Incorpora um arquivo de recurso gerenciado no assembly gerado.<br /><br />Essa opção de compilador é equivalente à opção de compilador c# do mesmo nome. Para obter mais informações, consulte [ &#47;recurso &#40;C&#35; opções do compilador&#41;](https://msdn.microsoft.com/library/c0tyye07.aspx).|
|**--sig**:&lt;**signature-filename&gt;**|Gera um arquivo de assinatura com base no assembly gerado. Para obter mais informações sobre arquivos de assinatura, consulte [assinaturas](signatures.md).|
|**--simpleresolution**|Especifica que as referências de assembly devem ser resolvidas usando regras Mono baseadas em diretório, em vez da resolução do MSBuild. O padrão é usar a resolução do MSBuild exceto quando em execução em Mono.|
|**--standalone**|Especifica para produzir um assembly que contém todas as suas dependências para que ele é executado por si só, sem a necessidade de assemblies adicionais, como a biblioteca F #.|
|**--staticlink:&lt;assembly-name**&gt;|Vincula estaticamente o assembly fornecido e todas as DLLs referenciadas que dependem deste assembly. Use o nome do assembly, não o nome da DLL.|
|**--subsystemversion**|Especifica a versão do subsistema de sistema operacional a ser usado pelo executável gerado. Use 6.02 para Windows 8.1, 6.01 para Windows 7, 6.00 para o Windows Vista. Essa opção só se aplica a executáveis, DLLs não e precisa ser usada somente se seu aplicativo depende de recursos de segurança específicos disponíveis apenas em determinadas versões do sistema operacional. Se essa opção for usada, e um usuário tenta executar seu aplicativo em uma versão inferior do sistema operacional, ele falhará com uma mensagem de erro.|
|**--tailcalls**[**+**&#124;**-**]|Habilita ou desabilita o uso da instrução IL final, que faz com que o quadro de pilha ser reutilizado para funções de recursivas final. Essa opção é habilitada por padrão.|
|**--target**:[**exe** &#124; **winexe** &#124; **library** &#124; **module** ] **&lt;output-filename&gt;**|Especifica o tipo e o nome do código compilado gerado.<ul><li>**exe** significa que um aplicativo de console.<br /></li><li>**winexe** significa que um aplicativo do Windows, que é diferente do aplicativo de console, pois ele não tem padrão fluxos de entrada/saída (stdin, stdout e stderr) definidos.<br /></li><li>**biblioteca** é um assembly sem um ponto de entrada.<br /></li><li>**módulo** é um módulo do .NET Framework (. netmodule), que posteriormente pode ser combinado com outros módulos em um assembly.<br /></li><ul/>Essa opção de compilador é equivalente à opção de compilador c# do mesmo nome. Para obter mais informações, consulte [ &#47;destino &#40;C&#35; opções do compilador&#41;](https://msdn.microsoft.com/library/6h25dztx.aspx).|
|**--times**|Exibe informações de tempo de compilação.|
|**--utf8output**|Permite imprimir a saída de compilador em codificação UTF-8.|
|**--warn:&lt;warning-level&gt;**|Define um nível de aviso (0 a 5). O nível padrão é 3. Cada aviso é fornecido um nível com base em sua severidade. Nível 5 fornece avisos graves, mais, mas menor do que o nível 1.<br /><br />Avisos de nível 5: 21 (use recursiva verificada em tempo de execução), 22 (**permitem rec** avaliada fora de ordem), 45 (abstração completa) e 52 (cópia defesa). Todos os outros avisos são o nível 2.<br /><br />Essa opção de compilador é equivalente à opção de compilador c# do mesmo nome. Para obter mais informações, consulte [ &#47;Avisar &#40;C&#35; opções do compilador&#41;](https://msdn.microsoft.com/library/13b90fz7.aspx).|
|**--warnon:&lt;int-list&gt;**|Habilite avisos específicos que podem estar desativados por padrão ou desabilitado por outra opção de linha de comando. Em F # 3.0, apenas o aviso 1182 (variáveis não utilizadas) está desativado por padrão.|
|**--warnaserror**[**+**&#124;**-**] [**&lt;int-list&gt;**]|Habilita ou desabilita a opção de relatar avisos como erros. Você pode fornecer os números de avisos específicos para ser habilitado ou desabilitado. Opções mais tarde na linha de comando substituem as opções anteriores na linha de comando. Por exemplo, para especificar os avisos que você não deseja relatados como erros, especifique **– /warnaserror + - /warnaserror-:&lt;int lista&gt;**.<br /><br />Essa opção de compilador é equivalente à opção de compilador c# do mesmo nome. Para obter mais informações, consulte [ &#47;warnaserror &#40;C&#35; opções do compilador&#41;](https://msdn.microsoft.com/library/406xhdz3.aspx).|
|**--win32manifest:manifest-filename**|Adiciona um arquivo de manifesto Win32 para a compilação. Essa opção de compilador é equivalente à opção de compilador c# do mesmo nome. Para obter mais informações, consulte [ &#47;win32manifest &#40;C&#35; opções do compilador&#41;](https://msdn.microsoft.com/library/bb545961.aspx).|
|**--win32res:resource-filename**|Adiciona um arquivo de recurso Win32 à compilação.<br /><br />Essa opção de compilador é equivalente à opção de compilador c# do mesmo nome. Para obter mais informações, consulte [ &#47;win32res (&#40;C & #35); Opções do compilador&#41;](https://msdn.microsoft.com/library/8f2f5x2e.aspx).|

## <a name="related-topics"></a>Tópicos relacionados


|Título|Descrição|
|-----|-----------|
|[Opções do F# Interativo](fsharp-interactive-options.md)|Descreve as opções de linha de comando com suporte do interpretador de F #, fsi.exe.|
|[Referência de Propriedades do Projeto](/visualstudio/ide/reference/project-properties-reference)|Descreve a interface do usuário para projetos, incluindo páginas de propriedades de projeto que fornece opções de compilação.|
