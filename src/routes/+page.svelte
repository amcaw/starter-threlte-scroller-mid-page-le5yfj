<script>
  import ScrollerSections from '$lib/ScrollerSections.svelte';

</script>

<header>
  <h1>THRELTE SCROLLER</h1>
  <p>A long page with a scroll triggered canvas somewhere in the middle.</p>
</header>
<section>
  <h2>Keep Scrolling</h2>
  <p>Nothing fancy here, just some text.</p>
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ex possimus doloremque itaque obcaecati veritatis? Excepturi, error praesentium quas dolore, a asperiores quod sit minima quis, ullam dolorem laudantium cumque! Consequuntur commodi architecto ad ratione iusto minus molestiae animi maxime quae doloremque voluptatibus ab labore quisquam nesciunt delectus nam rem voluptate, blanditiis eum! Culpa ut iste voluptatum vel, fuga blanditiis id.</p>
</section>
<ScrollerSections />
<section>
  <h2>How does it work?</h2>
  <p>It's just a long page (as seen here in the <code>+page.svelte</code> file).</p>
  <p>There's a chunk in the middle that holds the canvas while you scroll (probably other ways to implement this!)</p>
  <p>Inside that section is all the scrolling interaction logic, handled by svelte-scroller and threlte</p>
</section>

<style>
 header, section {
   height: 80vh;
   color: #fafbfc;
   display: flex;
   flex-direction: column;
   justify-content: center;
   align-items: center;
 }
</style>