# AI-Managed Software Project Orchestrator

Codex veya Claude Code'un yalnızca kod yazmasını değil; bir yazılım projesini keşif, şartname, planlama, geliştirme, bağımsız QA ve production hazırlığı boyunca yönetmesini sağlayan yeniden kullanılabilir Skill.

## Ne sağlar?

- Boş klasör, mevcut repository ve migration projelerini ayrı biçimde ele alır.
- Projeyi riskine göre **Light**, **Standard** veya **High Assurance** olarak sınıflandırır.
- İş talebini test edilebilir gereksinimlere ve kabul kriterlerine dönüştürür.
- `AGENTS.md`, `CLAUDE.md` ve gerekli proje dokümanlarını AI'ın oluşturup güncel tutmasını sağlar.
- Şartname ve teknik plan onaylanmadan geliştirmeye başlanmasını engeller.
- Developer ile kaynak kodu değiştiremeyen bağımsız QA oturumunu ayırır.
- Test kanıtları, açık riskler, rollback ve release kontrolleri olmadan production hazır iddiasında bulunmaz.

Kullanıcı **Product Owner** ve nihai kabul makamıdır. Belgeleri kullanıcıya yazdırmak yerine AI hazırlar; kullanıcı yalnızca önemli ürün kararlarını ve geçiş kapılarını onaylar.

## Çalışma akışı

1. **Discovery:** İhtiyaçları, kısıtları, mevcut varlıkları ve riskleri belirler.
2. **Bootstrap:** Uygun talimat dosyalarını ve minimum proje dokümantasyonunu oluşturur.
3. **Specification:** Kapsamı, kullanıcı akışlarını, edge case'leri ve kabul kriterlerini netleştirir.
4. **Architecture & Plan:** Teknik yaklaşımı ve doğrulanabilir geliştirme adımlarını planlar.
5. **Build:** Yalnızca onaylanmış kapsamı küçük ve test edilebilir parçalar halinde geliştirir.
6. **Independent QA:** Ayrı ve mümkünse salt okunur bir oturumda inceleme yürütür.
7. **Release Readiness:** Test, güvenlik, erişilebilirlik, yapılandırma, migration, gözlemlenebilirlik ve rollback kanıtlarını toplar.

Her kritik aşama bir karar paketiyle Product Owner onayına sunulur.

## Kurulum

Repository özel olduğu için GitHub hesabınızın terminalde yetkilendirilmiş olması gerekir.

### Codex ve Claude Code'a tek komutla kurulum

[`skills`](https://skills.sh) CLI, Skill'i global olarak kurar ve iki aracın doğru dizinlerini otomatik yönetir:

```bash
npx skills add https://github.com/doruksucuka/orchestrate-software-project \
  --skill orchestrate-software-project \
  --global \
  --agent codex \
  --agent claude-code \
  --yes
```

### Yalnızca Codex

```bash
npx skills add https://github.com/doruksucuka/orchestrate-software-project \
  --skill orchestrate-software-project --global --agent codex --yes
```

### Yalnızca Claude Code

```bash
npx skills add https://github.com/doruksucuka/orchestrate-software-project \
  --skill orchestrate-software-project --global --agent claude-code --yes
```

`--global` Skill'i tüm projelerde kullanılabilir yapar. `--yes` etkileşimli onayları atlar; hedef araçları kendiniz seçmek isterseniz bu parametreyi kaldırabilirsiniz.

Kurulumu doğrulamak için:

```bash
npx skills list --global
```

## Kullanım

Codex:

```text
$orchestrate-software-project
```

Claude Code:

```text
/orchestrate-software-project
```

Örnek başlangıç talebi:

```text
Yeni bir projeye başlıyoruz. Bu boş klasörde süreci uçtan uca yönet.
Önce iş talebini analiz et, uygun güvence profilini öner ve bootstrap aşamasını yürüt.
Şartname ve plan onaylanmadan uygulama kodu yazma.
```

Skill, açıklamasıyla eşleşen kapsamlı proje başlatma ve yönetme taleplerinde otomatik olarak da seçilebilir. Tek dosyalık düzenlemeler veya dar kapsamlı hata düzeltmeleri için tasarlanmamıştır.

## Güncelleme

```bash
npx skills update orchestrate-software-project --global --yes
```

## Repository yapısı

```text
orchestrate-software-project/
├── README.md
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── delivery-lifecycle.md
    ├── executor-adapters.md
    └── risk-profiles.md
```

- `README.md`: Kurulum, kullanım ve repository özeti.
- `SKILL.md`: Ana orkestrasyon kuralları ve yaşam döngüsü.
- `agents/openai.yaml`: Codex/ChatGPT arayüz metadatası.
- `references/delivery-lifecycle.md`: Orantılı teslimat aşamaları ve karar kapıları.
- `references/executor-adapters.md`: Codex, Claude Code ve çift araç kullanım biçimleri.
- `references/risk-profiles.md`: Light, Standard ve High Assurance sınıflandırması.

## Önemli sınır

Bu Skill; hukuk, mevzuat, sızma testi, güvenlik uzmanlığı veya alan uzmanlığı gerektiren profesyonel kontrollerin yerine geçmez. Yüksek riskli projelerde gerekli insan uzman incelemelerini sürece dahil eder.
