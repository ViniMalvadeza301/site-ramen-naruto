VINICIUS LIMA CARNEIRO

O projeto foi feito seguindo uma temática do anime Naruto, mais especificamente de um dos personagens mais carismaticos do anime, Ichiraku que é uma das primeiras figuras que oferecem ajuda ao protagonista Naruto, além disso trabalha fazendo diversos tipos de ramens e vendendo por toda vila de Konoha alegrando os ninjas e o povo da vila.

function banco() {
    const dados = [
        { id: 0, nome: 'vini', email: 'vini@gmail.com', senha: '123' },
        { id: 1, nome: 'ringo', email: 'ringo@gmail.com', senha: '1234' },
        { id: 2, nome: 'bruno', email: 'bruno@gmail.com', senha: '12345' }
    ];
    let meuJson = JSON.stringify(dados);
    localStorage.setItem("bancodados", meuJson);
}

function logar() {
    const nm = document.querySelector("#nome").value;
    const sn = document.querySelector("#senha").value;

    let dados = JSON.parse(localStorage.getItem("bancodados"));
    
    let acessoPermitido = false;
    let usuarioLogado = null;

    for (let i = 0; i < dados.length; i++) {
        if (nm === dados[i].nome && sn === dados[i].senha) {
            acessoPermitido = true;
            usuarioLogado = dados[i].nome; // Armazena o nome do usuário
            break;
        }
    }

    if (acessoPermitido) {
        alert('Acesso permitido');
        sessionStorage.setItem("usuario", usuarioLogado); // Armazena o nome antes de redirecionar
        window.location.href = "index.html"; // Redireciona em seguida
        console.log(sessionStorage.getItem("usuario"));
    } else {
        alert('Credenciais inválidas');
    }
}


function userLogado(){
    document.querySelector("#bemvindo").value = sessionStorage.getItem("usuario");
}
