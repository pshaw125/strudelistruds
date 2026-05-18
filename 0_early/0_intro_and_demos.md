// Mix of samples from reference docs and "In the Beginning" (Switch Angel - https://www.youtube.com/watch?v=YFQm8Hk73ug)

// _$: s("[bd <hh oh>]*2").bank("tr909").dec(.4)
// cpm(60)
// note("a2 c3 d3 c3")
// .s("sawtooth")
// .lpf(1200)

setCpm(136/4)
register('acidenv', (x, pat) => 
  pat.lpf(100)
  .lpenv(x*9)
  //.lpsustain(slider(0.5,0,1,0.05))
  .lpsustain("<0 .25 .5 1>/4") //Sets the sustain amplitude for the lowpass filter envelope.
  .lpdecay("<.5 .25 .1 0>/3") //Sets the decay duration for the lowpass filter envelope.
)

$: n("<0 <2 7 0 9>>*8").scale("<c:minor, g:minor>")
  .trans(-12)
  .orbit(3)
  .sound("sawtooth")
  .acidenv(slider(0.5, 0.1, 1, 0.05))
  ._pianoroll()

// note("d1!8").s("sine").penv(36).pdecay(.12).decay(.23).distort("8:.4")

