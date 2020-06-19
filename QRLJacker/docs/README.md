Bem, trabalhei duro para tornar o desenvolvimento o mais simples possível e você verá que :smile:
> Antes de começar, verifique se você ativou o modo de desenvolvimento. Se você fez isso, a estrutura recarregará o módulo toda vez que você executá-lo com as novas alterações sem precisar reiniciar a estrutura

# Escrevendo um módulo de captura para o Framework
- Grabber Os módulos são os principais módulos da estrutura e estão no diretório `core/modules/grabber`
- Depois de adicionar qualquer arquivo python, ele é carregado na estrutura com três opções automaticamente. As três opções são (é claro) host, porta e useragent
- O código dentro do arquivo do módulo deve ser o seguinte:

```
# -*- coding: utf-8 -*-
from core.module_utils import types

class info:
    author            = ""               # (1)
    short_description = ""               # (2)
    full_description  = None             # (3)

class execution:
    module_type       = types.grabber
    name              = ""               # (4)
    url               = ""               # (5)
    image_xpath       = ""               # (6)
    img_reload_button = None             # (7)
    change_identifier = ""               # (8)
    session_type      = "localStorage"   # (9)

```

As variáveis ​​de código são descritas abaixo:
1. Aqui você adiciona seu nome que aparecerá na estrutura
2. Aqui você coloca uma breve descrição rápida que aparecerá ao listar os Módulos
3. Aqui você coloca a Descrição completa em seu módulo, se necessário, e ela aparecerá apenas ao usar o `info` comando. Se você não adicionar um, deixe-o como Nenhum e a breve descrição será usada.
4. O nome do site que será usado dentro da estrutura e também você deve criar uma pasta com o mesmo nome que o valor da variável no caminho `core/www` exemplo: `core/www/whatsapp`
5. O URL que possui o QR Code e usado para carregar o exemplo da sessão: `https://web.whatsapp.com`
6. O xpath exato para a posição da imagem QR na página, porque ele será usado pela estrutura para capturar a imagem da imagem QR.
7. Se este site estiver inativo e quiser que você clique em atualizar a cada poucos minutos como o whatsapp, por exemplo, coloque o xpath exato para esse botão quando ele aparecer e a estrutura executará um thread para verificar a cada poucos segundos a aparência do botão recarregar e clique nele. Se essa técnica não for usada, deixe a variável como Nenhuma.
8. O xpath de um elemento na página desaparece apenas quando a sessão é carregada. Por exemplo, a tag img do QR Code no whatsapp.
9. Essa variável assume um dos dois valores `localStorage` ou `Cookies`. O valor deve ser o mesmo usado no site para determinar a sessão do usuário.

E pronto! Você criou seu primeiro módulo. Você pode mantê-lo por conta própria ou melhor criar um PR para a estrutura, para que todos possam usar seu módulo com o seu nome, faça as contas :smile:
