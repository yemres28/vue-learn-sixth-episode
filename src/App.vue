<template>
  <div class="container">
    <div class="row">
      <div class="col-md-6 col-md-offset-3">
        <!-- Slot kullanımı çok kolay child components imizi 
        parent componentinde import edip kullanmak için 
        html template bloğunda kullanıyoruz. daha sonrasında
        tek satırda kapatmak yerinde bir div gibi önce açıp 
        sonra da kapatıyoruz ve içine istediğimiz html taglarini
        işlemleri yapıyoruz daha sonrasında ise bunu kullanmak için 
        child components da slot deyip açıp kapamak yeterli olucak . -->

        <!-- Bir slotu isimlendirerek sadece istediğmiz yerde görünmesini sağlayabiliriz.
        Örnek aşağıda ve HomeView Sayfasında  -->
        <br /><br />
        <button
          @click="selectedComponent = 'MemoryVue'"
          class="btn-sm btn btn-primary"
        >
          Memory Page
        </button>
        <button
          @click="selectedComponent = 'NewMemory'"
          class="btn-sm btn btn-primary"
        >
          New Memory Page
        </button>
        <button
          @click="selectedComponent = 'AuthorVue'"
          class="btn-sm btn btn-primary"
        >
          Author Page
        </button>

        <hr />
        <p>{{ selectedComponent }}</p>
        <hr />

        <!-- dinamik componentlerde bir başka sayfaya geçtiğin zaman componentin yaşam döngüsü life cycle ölüyor eğer biz
        componentin sürekli kalmasını life cycle ın ölmesini istemiyorsak yapmamız gereken şey çok basit
        component tagimizi keep alive tagine sarıyoruz
        
        fakat keep alive tag ini kullanığımızda life cycle hook yine kayboluyor fakat
        vue bunun için bize activated ve deactivated adında iki yeni hook sağlamış bu hooklar aşağıdaki gibi kullanılıyor

        script kısmında 

        activated : {
          code block
        }
        deactivated : {
          code block
        }
         -->
        <keep-alive>
          <component :is="selectedComponent">
            <h3>Slot ile verip göndermek</h3>
            <p>Slot denemesi</p>
            <p><b slot="NamedSlot">Named Slot Örneği"</b></p>
          </component>
        </keep-alive>
        <!-- <memory-vue content="Vue ile prop gönderimi">
          <h3>Slot ile verip göndermek</h3>
          <p>Slot denemesi</p>
          <p><b slot="NamedSlot">Named Slot Örneği"</b></p>
        </memory-vue>
        <author-vue />
        <new-memory /> -->
      </div>
    </div>
  </div>
</template>
<script>
import MemoryVue from "@/views/MemoryVue.vue";
import AuthorVue from "@/views/AuthorVue.vue";
import NewMemory from "@/views/NewMemory.vue";
// Bu dersin konuları bue js de slot kullanımı yani prop olarak html tagları propertyler nasıl gönderilir
export default {
  components: {
    MemoryVue,
    AuthorVue,
    NewMemory,
  },
  data() {
    return {
      selectedComponent: "MemoryVue",
    };
  },
};
</script>
