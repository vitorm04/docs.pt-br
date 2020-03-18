---
title: Assinar um assembly com atraso
ms.date: 08/19/2019
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 113df1ad3fc3ac1e27ebfef572494c1f15a3dbb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73733167"
---
# <a name="delay-sign-an-assembly"></a>Assinar um assembly com atraso

Uma organização pode ter um par de chaves bem guardado que os desenvolvedores não podem acessar diariamente. A chave pública normalmente está disponível, mas o acesso à chave privada é restrito a apenas algumas pessoas. Ao desenvolver assemblies com nomes fortes, cada assembly que referencia o assembly de destino com nome forte contém o token da chave pública usada para fornecer ao assembly de destino um nome forte. Isso requer que a chave pública esteja disponível durante o processo de desenvolvimento.

Você pode usar a assinatura atrasada ou parcial no tempo de construção para reservar espaço no arquivo executável portátil (PE) para a assinatura do nome forte, mas adiar a assinatura real até algum estágio posterior, geralmente pouco antes de enviar o conjunto.

Para atrasar a sinalização de uma assembléia:

1. Obtenha a parte de chave pública do par-chave da organização que fará a eventual assinatura. Normalmente, essa chave está na forma de um arquivo *.snk,* que pode ser criado usando a [ferramenta Nome Forte (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) fornecida pelo Windows SDK.

2. Anote o código-fonte para o assembly com dois atributos personalizados de <xref:System.Reflection>:

   - <xref:System.Reflection.AssemblyKeyFileAttribute>, que passa o nome do arquivo que contém a chave pública como um parâmetro para seu construtor.

   - <xref:System.Reflection.AssemblyDelaySignAttribute>, o que indica que a assinatura de atraso está sendo usada passando **verdadeiro** como parâmetro para seu construtor.

   Por exemplo: 

   ```cpp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")];
   [assembly:AssemblyDelaySignAttribute(true)];
   ```

   ```csharp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")]
   [assembly:AssemblyDelaySignAttribute(true)]
   ```

   ```vb
   <Assembly:AssemblyKeyFileAttribute("myKey.snk")>
   <Assembly:AssemblyDelaySignAttribute(True)>
   ```

3. O compilador insere a chave pública no manifesto do assembly e reserva espaço no arquivo PE para a assinatura de nome forte completo. A chave pública real deve ser armazenada enquanto o assembly é compilado para que outros assemblies que referenciam esse assembly possam obter a chave para armazenar em sua própria referência do assembly.

4. Como o assembly não tem uma assinatura de nome forte válida, a verificação dessa assinatura deve ser desativada. Você pode fazer isso usando a opção **– Vr** com a ferramenta Nome Forte.

     O exemplo a seguir desativa a verificação de uma montagem chamada *myAssembly.dll*.

   ```console
   sn –Vr myAssembly.dll
   ```

   Para desligar a verificação em plataformas em que você não pode executar a ferramenta Nome Forte, como microprocessadores ARM (Advanced RISC Machine), use a opção **–Vk** para criar um arquivo de Registro. Importe o arquivo de Registro para o Registro no computador em que você deseja desligar a verificação. O exemplo a seguir cria um arquivo de Registro para `myAssembly.dll`.

   ```console
   sn –Vk myRegFile.reg myAssembly.dll
   ```

   Com a opção **–Vr** ou **–Vk),** você pode incluir opcionalmente um arquivo *.snk* para assinatura de chave de teste.

   > [!WARNING]
   > Por segurança, não confie em nomes fortes. Eles apenas fornecem uma identidade exclusiva.

   > [!NOTE]
   > Se você usar o atraso de assinatura durante o desenvolvimento com o Visual Studio em um computador de 64 bits e compilar um assembly para **Qualquer CPU**, talvez seja necessário aplicar a opção **-Vr** duas vezes. (No Visual Studio, **qualquer CPU** é um valor da propriedade de compilação de destino de **plataforma;** quando você compila a partir da linha de comando, é o padrão.) Para executar seu aplicativo a partir da linha de comando ou do File Explorer, use a versão de 64 bits da [ferramenta Sn.exe (Strong Name)](../../framework/tools/sn-exe-strong-name-tool.md) para aplicar a opção **-Vr** ao conjunto. Para carregar o assembly no Visual Studio no tempo de design (por exemplo, se o assembly contiver componentes que são usados por outros assemblies em seu aplicativo), use a versão de 32 bits da ferramenta de nome forte. Isso ocorre porque o compilador JIT (Just-in-time) compila o assembly para código nativo de 64 bits quando o assembly é executado da linha de comando e para código nativo de 32 bits quando o assembly é carregado no ambiente de tempo de design.

5. Posteriormente, normalmente imediatamente antes do envio, você envia o assembly para a autoridade de assinatura da sua organização para a assinatura de nome forte real usando a opção **–R** com a ferramenta Nome Forte.

   O exemplo a seguir assina um conjunto chamado *myAssembly.dll* com um nome forte usando o par de tecla *sgKey.snk.*

   ```console
   sn -R myAssembly.dll sgKey.snk
   ```

## <a name="see-also"></a>Confira também

- [Criar assemblies](create.md)
- [Como criar um par de chaves pública/privada](create-public-private-key-pair.md)
- [Sn.exe (ferramenta Nome Forte)](../../framework/tools/sn-exe-strong-name-tool.md)
