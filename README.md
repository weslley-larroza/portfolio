# portfolio

Site de apresentação pessoal de **Weslley Larroza**: Desenvolvedor Full Stack & Automação.
Página estática (HTML/CSS puro, sem build), publicada em https://weslleylarroza.com.br (Hostinger).

## Estrutura

| Arquivo | O que é |
| --- | --- |
| `index.html` | O site inteiro (estilos inclusos) |
| `cv/Weslley-Larroza-CV.pdf` | Currículo baixado pelos botões "Baixar CV" (adicionar) |
| `certificados/` | PDFs dos cursos listados na seção Formação |
| `assets/img/` | Prints dos projetos e `og.png` (prévia de link 1200×630) |
| `assets/fonts/` | Fontes hospedadas no próprio site (Bricolage Grotesque e Instrument Sans, licença OFL) |
| `robots.txt`, `sitemap.xml` | Indexação no Google |
| `.htaccess` | Força HTTPS, bloqueia listagem de pastas, cache |
| `.github/workflows/deploy-hostinger.yml` | Deploy automático por FTP a cada push na `main` |

## Ver localmente

```bash
python -m http.server 8000
# abrir http://localhost:8000
```

## Publicar na Hostinger

1. **Domínio:** no hPanel, adicione o domínio ao plano (Websites > Adicionar site) e, se ele foi
   registrado fora da Hostinger, aponte os nameservers para `ns1.dns-parking.com` e `ns2.dns-parking.com`.
2. **SSL:** hPanel > Segurança > SSL > instalar o certificado grátis para o domínio.
3. **Conta FTP:** hPanel > Arquivos > Contas FTP. Anote host, usuário e senha.
4. **Secrets no GitHub:** Settings > Secrets and variables > Actions > New repository secret:
   - `FTP_SERVER` · `FTP_USERNAME` · `FTP_PASSWORD`
   - `FTP_DIR` (opcional) se o site não for a raiz do domínio, ex.: `./domains/weslleylarroza.com.br/public_html/`
5. Faça push na `main` (ou rode o workflow em Actions > Deploy na Hostinger > Run workflow).

> Se o plano for **VPS**, o mesmo workflow funciona com um servidor FTP (vsftpd) instalado,
> ou dá para trocar o passo de FTP por `rsync` via SSH.

O GitHub Pages foi desativado: desligue em Settings > Pages para não ficar com dois endereços.

## Pendências

- [x] Adicionar o PDF do currículo em `cv/`
- [ ] (Opcional) trocar o e-mail do Outlook por um e-mail no domínio
- [ ] Atualizar o LinkedIn com o cargo atual

## Adicionar um certificado

1. Copie o PDF para `certificados/` com um nome curto (ex.: `docker-fundamentos.pdf`).
2. No `index.html`, duplique uma linha `<li data-area="...">` da lista `cert-list` e ajuste nome, horas, data e link.
   Áreas: `ia`, `dev`, `dados`, `infra`.
3. Atualize o total de certificados e horas no texto da seção.
